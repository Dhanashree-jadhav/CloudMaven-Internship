# • Lab 1 I configured SSH key-based authentication and disabled password login for security hardening.
```bash
🔹 Steps Performed
1️⃣ Started WSL (Ubuntu)
wsl --list --verbose
wsl
2️⃣ Updated System Packages
sudo apt update && sudo apt upgrade -y
3️⃣ Installed OpenSSH Server
sudo apt install openssh-server -y
4️⃣ Started and Enabled SSH Service
sudo systemctl start ssh
sudo systemctl enable ssh
sudo systemctl status ssh
5️⃣ Generated SSH Keys
ssh-keygen

Generated:

~/.ssh/id_ed25519 (Private Key)

~/.ssh/id_ed25519.pub (Public Key)

6️⃣ Enabled Passwordless Login
cat ~/.ssh/id_ed25519.pub >> ~/.ssh/authorized_keys
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
7️⃣ Tested SSH Login
ssh student@localhost

✅ Successfully connected via SSH using key-based authentication.
```
<img width="1920" height="1080" alt="day_2_lab_1 1" src="https://github.com/user-attachments/assets/6be7206e-33bc-4763-993d-dda13d26e90b" />
<img width="1920" height="1080" alt="day_2_lab_1 2" src="https://github.com/user-attachments/assets/02e3daec-5657-42fb-811d-aa0067d2289f" />
<img width="1920" height="1080" alt="day_2_lab_1 3" src="https://github.com/user-attachments/assets/87c05eed-30f0-4af5-9c34-a1e67dc990b8" />
<img width="1920" height="1080" alt="day_2_lab_1 4" src="https://github.com/user-attachments/assets/96d2f38d-ef23-418e-8f76-a62bcd34e626" />
<img width="1303" height="573" alt="day_2_lab_1 5" src="https://github.com/user-attachments/assets/57cb5d87-fe14-4842-9262-72f01e4ae0da" />

# • Lab 2, I scheduled a cron job that appends output to a log file every 5 minutes.
```bash
🔹 Task Created

Append the word "Test" to a file every 5 minutes.

1️⃣ Opened Crontab Editor
crontab -e
2️⃣ Added Cron Entry
*/5 * * * * echo "Test" >> /tmp/test.log
🕒 Cron Format Explanation
* * * * * command
| | | | |
| | | | └── Day of Week
| | | └──── Month
| | └────── Day of Month
| └──────── Hour
└────────── Minute

*/5 → Every 5 minutes

3️⃣ Verified Output
cat /tmp/test.log

Output:

Test
Test
```
<img width="1920" height="1080" alt="day_2_lab_2" src="https://github.com/user-attachments/assets/90d109c5-8dd7-4f85-9639-ad0e91eda69a" />

# • Lab 3, I created a custom systemd service and timer to execute a script periodically.
```bash
Part A – systemd Service & Timer
1️⃣ Created Script
sudo nano /usr/local/bin/systemd-test.sh

Script content:

#!/bin/bash
echo "Hello Systemd" >> /tmp/systemd.log

Made executable:

sudo chmod +x /usr/local/bin/systemd-test.sh
2️⃣ Created Service File
sudo nano /etc/systemd/system/systemd-test.service
3️⃣ Created Timer File
sudo nano /etc/systemd/system/systemd-test.timer
4️⃣ Reloaded systemd & Enabled Timer
sudo systemctl daemon-reload
sudo systemctl enable --now systemd-test.timer
5️⃣ Checked Timers
systemctl list-timers
6️⃣ Verified Output
cat /tmp/systemd.log

Output:

Hello Systemd
```
<img width="1918" height="686" alt="day_2_lab_3" src="https://github.com/user-attachments/assets/090a9663-b541-4feb-ac46-70427ee5b7c6" />


