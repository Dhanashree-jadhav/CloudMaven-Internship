# 🧪 Linux Networking & Automation Lab

This internship task covers:

- Disk monitoring using Bash scripting
- Capturing HTTP traffic using tcpdump
- Understanding TCP 3-way handshake
- Scheduling jobs using Cron

---

# 📌 Lab 1 — Disk Monitoring Script

## 🎯 Objective
Create a Bash script that monitors disk usage and logs an alert if usage exceeds a threshold.

## 📝 Script: disk_check.sh

```bash
#!/bin/bash
set -eu

threshold=80

usage=$(df / | awk 'NR==2 {print $5}' | sed 's/%//')
⚙️ Make Script Executable
chmod +x disk_check.sh
▶️ Run Script
./disk_check.sh
📊 What It Does

Uses df / to check root disk usage

Extracts percentage using awk and sed

Logs alert if usage > threshold
```
<img width="1917" height="512" alt="image" src="https://github.com/user-attachments/assets/d57364e4-7766-402f-b541-4a30fb5cfba1" />

# 🌐 Lab 2 — Capture HTTP Traffic
```bash
🎯 Objective

Capture HTTP packets and analyze TCP handshake using tcpdump.

🛠 Install tcpdump
sudo apt update
sudo apt install tcpdump
🔍 Identify Network Interface
ip a

(Interface used: eth0)

📡 Start Packet Capture
sudo tcpdump -i eth0 port 80 -n
🌍 Generate HTTP Traffic
curl http://example.com
🔥 Observed TCP 3-Way Handshake

SYN

SYN-ACK

ACK

📦 Observed HTTP Communication

HTTP GET request

HTTP/1.1 200 OK response

FIN packets (connection termination)
```
<img width="1919" height="845" alt="image" src="https://github.com/user-attachments/assets/f96ee388-d04e-42f8-a7b5-9a2e1ab57637" />
<img width="1467" height="159" alt="image" src="https://github.com/user-attachments/assets/5db46ca6-424c-4aa8-a7e8-9c5c167ffb20" />

# 🏠 Homework / Deliverables

This section covers additional Linux tasks related to scripting, process monitoring, log analysis, and job scheduling.

---

# 1️⃣ countargs.sh — Argument Counter Script

## 🎯 Objective
Create a Bash script that prints all command-line arguments and displays the total count.

## 📝 Script

```bash
#!/bin/bash

for arg in "$@"
do
    echo "$arg"
done

echo "Total arguments: $#"
```
<img width="1918" height="466" alt="image" src="https://github.com/user-attachments/assets/8a904e2a-be9e-4c84-bf00-089a17236910" />

```bash
2️⃣ Find Process Using Most Memory
🎯 Objective

Identify the process consuming the highest memory.

🛠 Command
ps aux --sort=-%mem | head -1
📚 Explanation

ps aux → List all running processes

--sort=-%mem → Sort by memory usage (descending)

head -1 → Display top process

3️⃣ Largest Directory in /var/log
🎯 Objective

Find the largest directory inside /var/log.

🛠 Command
du -sh /var/log/* | sort -hr | head -1
📚 Explanation

du -sh → Show directory size (human readable)

sort -hr → Sort by size (largest first)

head -1 → Display largest directory

4️⃣ View Last 20 SSH Logs
🎯 Objective

Check recent SSH service logs.

🛠 Command
journalctl -u ssh -n 20

(On some systems use sshd instead of ssh)

📚 Explanation

journalctl → View system logs

-u ssh → Filter SSH service logs

-n 20 → Show last 20 entries
```
<img width="1919" height="693" alt="image" src="https://github.com/user-attachments/assets/3babdd57-83f5-4548-b08d-ae1834dce687" />

```bash
5️⃣ Schedule Script Using Cron
🎯 Objective

Run disk monitoring script automatically every 5 minutes.

🛠 Edit Crontab
crontab -e
⏳ Add Entry
*/5 * * * * /home/student/disk_check.sh
🔎 Verify Cron Job
crontab -l
🔁 Alternative: Using systemd Timer
📁 disk_check.service
[Unit]
Description=Disk Usage Check Script

[Service]
ExecStart=/home/student/disk_check.sh
📁 disk_check.timer
[Unit]
Description=Run disk check every 5 minutes

[Timer]
OnBootSec=1min
OnUnitActiveSec=5min

[Install]
WantedBy=timers.target
▶️ Enable & Start Timer
sudo systemctl daemon-reload
sudo systemctl enable disk_check.timer
sudo systemctl start disk_check.timer
```
<img width="1919" height="985" alt="image" src="https://github.com/user-attachments/assets/f1007340-fd5a-43b3-8515-0c62407bb3eb" />

