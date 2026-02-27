# 🐧 Linux Assessment – DevOps Evaluation

## 👩‍💻 Candidate
**Name:** Dhanashree Jadhav  
**Batch:** 2026-02  
**Environment Used:** Ubuntu (Linux VM)

---

# 📌 1. Permissions & umask

## a) Create test.txt
```bash
touch test.txt
ls -l test.txt
Output:
-rw-r--r-- 1 user user 0 Feb 27 10:00 test.txt
b) umask
umask
Output:
0022
Explanation:

Default file permission = 666
Umask = 022
Final Permission = 666 - 022 = 644
So file permission becomes rw-r--r--.
```

<img width="1917" height="228" alt="test1" src="https://github.com/user-attachments/assets/27f17394-74bc-46f4-90cf-e4d8045ab1a4" />

#  2. User Management
```bash
🔹 Create user intern1 with bash shell and 7-day expiry
sudo useradd -m -s /bin/bash -e $(date -d "+7 days" +%Y-%m-%d) intern1
Explanation:

-m → Creates home directory

-s /bin/bash → Sets default shell

-e → Sets account expiry date

Verify:

chage -l intern1

This confirms account expiration date.
```
<img width="1918" height="692" alt="test_2 1" src="https://github.com/user-attachments/assets/f6454fde-d39a-40c1-950e-55203bf7eda9" />

# 3. SSH Configuration
```bash
🔹 Generate SSH key pair
ssh-keygen -t rsa -b 4096
Explanation:

Generates private & public key.

Used for passwordless authentication.

🔹 Enable passwordless SSH to localhost
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

Test:

ssh -i ~/.ssh/id_rsa localhost

If login happens without password → configuration successful.
```
<img width="1918" height="976" alt="test2 2" src="https://github.com/user-attachments/assets/87352c76-cfcf-4238-9df0-551075e07cbb" />

# 📌 4. Package Management
```bash
🔹 Install htop
sudo apt update
sudo apt install -y htop
Explanation:

apt update refreshes package list.

apt install installs the package.

🔹 Find which package provides /bin/bash
dpkg -S /bin/bash
Explanation:

dpkg -S searches installed packages that contain a specific file.
```

# 📌 5. Cron Job
```bash
🔹 Create a cron job to run every minute
crontab -e

Add:

* * * * * /usr/bin/date >> /tmp/cron_test.log
Explanation:

* * * * * → Every minute

Appends date output to /tmp/cron_test.log

Verify:

crontab -l
```
<img width="1911" height="387" alt="image" src="https://github.com/user-attachments/assets/11503963-88c8-451b-bfdb-096a4c713ecb" />

# 📌 6. Systemd Timer
```bash
🔹 Created Service File

/etc/systemd/system/hello.service

Executes:

echo "Hello from systemd" >> /tmp/hello.txt
🔹 Created Timer File

/etc/systemd/system/hello.timer

Runs service every 2 minutes.

Enable timer:

sudo systemctl daemon-reload
sudo systemctl enable --now hello.timer
systemctl list-timers
Explanation:

Systemd timers are modern replacements for cron with better logging and dependency management.
```
<img width="1915" height="950" alt="image" src="https://github.com/user-attachments/assets/84e460d7-6fe8-4608-a065-9baa730cddd9" />

# 📌 7. Networking
```bash
🔹 Ping Google DNS
ping -c 1 8.8.8.8

Checks connectivity.

🔹 Traceroute
traceroute example.com

Shows path packets take to reach destination.

🔹 Show Listening Ports
ss -tulnp

Displays active TCP/UDP listening services.

🔹 Capture HTTP Traffic
sudo tcpdump -i any port 80 -c 5 -w /tmp/http.pcap

Captures 5 HTTP packets.

🔹 Block Specific IP to Port 80
sudo ufw deny from 10.0.2.55 to any port 80
sudo ufw status

Adds firewall rule.

🔹 Check Headers & DNS
curl -I http://example.com
dig +short example.com

curl -I shows HTTP response headers.

dig +short shows A record.
```
<img width="1913" height="117" alt="image" src="https://github.com/user-attachments/assets/2fd559b2-192a-45f1-8ae3-9a01d42a7f2e" />
<img width="1912" height="601" alt="image" src="https://github.com/user-attachments/assets/0f1c7b04-ff6b-48c7-821b-539185f34ab8" />
<img width="1455" height="105" alt="image" src="https://github.com/user-attachments/assets/10a8020e-6705-4ca6-828d-847fa4140a23" />

# 📌 8. Monitoring
```bash
🔹 Disk Usage
df -h
du -sh /var/log

df -h → Filesystem usage

du -sh → Directory size

🔹 Top 3 Memory Processes
ps aux --sort=-%mem | head -4

Sorted by memory usage in descending order.

🔹 System Logs
journalctl -n 20
tail -n 20 /var/log/syslog
```
<img width="1918" height="970" alt="image" src="https://github.com/user-attachments/assets/0b70be56-f073-4f6e-a766-5cacc599dfe6" />
<img width="1913" height="467" alt="image" src="https://github.com/user-attachments/assets/0ae97329-f40c-49ad-9b37-f32815011def" />

# 📌 9. Log Locations
```bash
If installed:

Apache:

/var/log/apache2/access.log
/var/log/apache2/error.log

Nginx:

/var/log/nginx/access.log
/var/log/nginx/error.log

Displays latest system log entries.
```
<img width="1911" height="814" alt="image" src="https://github.com/user-attachments/assets/55666538-9351-41ad-a0db-9bffe02a8ae0" />

# 📌 10. Network Troubleshooting
```bash
sudo tcpdump -i any tcp port 80 -w http.pcap

Captures only HTTP traffic.
```
<img width="1917" height="668" alt="image" src="https://github.com/user-attachments/assets/c680a0a6-8916-46e8-88fa-2c6d2479ba04" />

# 📌 11. Bash Script – Disk Check
```bash
/tmp/check_disk.sh

#!/bin/bash

usage=$(df / | awk 'NR==2 {print $5}' | tr -d '%')

if [ "$usage" -gt 80 ]; then
    echo "Disk almost full" >&2
    exit 1
else
    echo "Disk OK"
    exit 0
fi
Explanation:

Extracts root / usage.

If usage > 80% → prints error to stderr and exits with code 1.

Otherwise prints OK and exits with 0.
```
<img width="1915" height="90" alt="image" src="https://github.com/user-attachments/assets/e657dbe4-6fff-4814-8d79-6b172a47529a" />
<img width="1903" height="325" alt="image" src="https://github.com/user-attachments/assets/806cf10c-4d5c-4854-a82d-4c2ef72f9d87" />

