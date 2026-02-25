# 🧪 Lab 1 – User Management
```bash
🎯 Objective

Learn how to create and manage users in Linux.

🔹 1️⃣ Create a New User
sudo adduser devuser

📌 What it does:

Creates a new user

Creates a home directory /home/devuser

Sets password

🔹 2️⃣ Switch User
su - devuser

📌 What it does:

Switches to the new user

Loads that user's environment

🔹 3️⃣ Verify Home Directory
pwd

Expected Output:

/home/devuser

📌 Confirms that the user has a proper home directory.
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c89a1f72-a3ce-4351-aa86-b04194021bb7" />


# 🧪 Lab 2 – File Permissions & Ownership
```bash
🎯 Objective

Understand Linux file permissions and ownership.

🔹 1️⃣ Create a File
touch testfile.txt
🔹 2️⃣ Check Permissions
ls -l testfile.txt

Example Output:

-rw-r--r-- 1 student student 0 Feb 25  testfile.txt

Permission Breakdown:

-rw-r--r--
| |  |  |
| |  |  └── Others
| |  └──── Group
| └──────── Owner
└────────── File Type
🔹 3️⃣ Modify Permissions
chmod 700 testfile.txt

Meaning:

Owner → Read, Write, Execute

Group → No permission

Others → No permission

🔹 4️⃣ Change Ownership
sudo chown devuser testfile.txt

Changes file owner to devuser.

🔹 5️⃣ Test Access

Switch to another user and try:

su - devuser
cat testfile.txt

📌 Verifies whether permissions work correctly.
```

# 🧪 Lab 3 – Process Control
```bash
🎯 Objective

Learn how to manage running processes.

🔹 1️⃣ Run a Background Process
sleep 300 &

📌 Runs a process in background for 300 seconds.

& → Runs command in background.

🔹 2️⃣ Identify Process ID (PID)
ps aux | grep sleep

OR

ps -ef

📌 Find the PID number.

🔹 3️⃣ Kill Process
kill <PID>

Example:

kill 1234

Force Kill (if needed):

kill -9 1234
```

# 🧪 Lab 4 – Editing Files Using Vim
```bash
🎯 Objective

Learn basic file editing using Vim editor.

🔹 1️⃣ Create a File
vim notes.txt
🔹 2️⃣ Insert Content

Press:

i

Type your content.

🔹 3️⃣ Save & Exit

Press:

ESC

Then type:

:wq

Press Enter.
```
