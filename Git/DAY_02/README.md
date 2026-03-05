# Git Practical – DevOps Learning
# Date : 5 march
# Name : Dhanashree Jadhav
# practice repo : https://github.com/Dhanashree-jadhav/git-practical.git

This repository demonstrates real-world Git scenarios and how to handle them properly in a team environment.

---

# 🔥 Scenario 1 – Wrong Branch Commit

## Situation
- Worked on `feature/login`
- Accidentally committed directly to `main`
- Commit was NOT pushed

## Solution
- Created new branch `feature/login`
- Used `git reset --soft HEAD~1`
- Switched to new branch
- Committed changes
- Pushed branch and created Pull Request
- Merged properly into `main`

## Commands Used
```bash
git branch feature/login
git reset --soft HEAD~1
git checkout feature/login
git commit -m "Added login feature"
git push -u origin feature/login
```
<img width="1209" height="767" alt="image" src="https://github.com/user-attachments/assets/21458674-59c7-44cb-a180-8b6c455a9f0f" />
<img width="1216" height="771" alt="image" src="https://github.com/user-attachments/assets/5f0c8a0e-6db4-4ff4-b42b-b51ba8feda8c" />
<img width="1918" height="971" alt="scenario_1 1" src="https://github.com/user-attachments/assets/18fd65d1-d5f3-49b9-b4fb-a46180e7d57c" />
<img width="1918" height="1037" alt="sce_1 2" src="https://github.com/user-attachments/assets/b2b11722-e4f5-49e2-b6cc-dca63f859c91" />

# 🔥 Scenario 2 – Bad Commit Already Pushed (Team-Safe Undo)

## 📌 Situation

1. Developer pushed changes to `main`
2. I pulled the latest changes
3. I made a wrong config change
4. I committed and pushed it to `main`
5. Team reported that the change was incorrect

The commit was already pushed to remote, so rewriting history was NOT allowed.

---

## ❌ What NOT To Do

```bash
git reset --hard HEAD~1
git push --force
```
<img width="1216" height="768" alt="image" src="https://github.com/user-attachments/assets/55124154-888d-4183-9fe5-0932bb91a2bd" />
<img width="1220" height="757" alt="image" src="https://github.com/user-attachments/assets/8113fc7d-7652-4100-9b47-80e59f024dc2" />
<img width="1206" height="753" alt="image" src="https://github.com/user-attachments/assets/424b8e80-e697-4352-9848-93f334e31d8d" />
<img width="1920" height="1080" alt="sce_2 1" src="https://github.com/user-attachments/assets/64d94a3f-1404-4cc8-a80b-f651996e3e84" />
<img width="1920" height="1026" alt="sce_2 2" src="https://github.com/user-attachments/assets/cc47424f-fce4-469f-9367-d7f048ebafee" />


---

# 🔥 Scenario 3 – Merge Conflict Handling

## 📌 Situation
```bash
1. Created branch `feature/payment`
2. Modified `app.txt`
3. Committed changes
4. Switched to `main`
5. Modified the SAME file
6. Tried merging `feature/payment` into `main`
7. Merge conflict occurred
```
# When you get a merge conflict, Git temporarily stores 3 versions of the file internally.

# During a merge conflict, Git keeps:

```bash Version	Meaning
Ours	Current branch version (where you are)
Theirs	Incoming branch version (the branch you're merging)
Base	Common ancestor version
```
---

## 💥 Conflict Message

<img width="1207" height="768" alt="image" src="https://github.com/user-attachments/assets/ea1b3fad-c23b-49f6-b973-a1fb197383e1" />
<img width="1211" height="770" alt="image" src="https://github.com/user-attachments/assets/49f6416c-23a5-49a0-b8a3-6b9f5b262351" />

```
