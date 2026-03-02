# Git Practical – Internship Task

## 👩‍💻 Name: Dhanashree Jadhav  
## 📅 Date: 2 March 2026  

---

## ✅ Task 1: Install Git

- Installed Git on local machine.
- Verified installation using:

```
git --version

```
<img width="1077" height="129" alt="Screenshot 2026-03-02 202331" src="https://github.com/user-attachments/assets/2b54607d-d8ce-4835-9804-ec33dc1c5c5a" />

---

## ✅ Task 2: Configure Git (Global & Local)

### 🔹 Global Configuration

Configured global username and email:

```
git config --global user.name "Dhanashree-jadhav"
git config --global user.email "dhanaa1611@gmail.com"
```

Verified using:

```
git config --global --list
```
<img width="1049" height="93" alt="image" src="https://github.com/user-attachments/assets/2e4c973c-1765-46bf-a51d-02ce085472c0" />

---

### 🔹 Local Configuration

Initialized repository:

```
git init
```
<img width="1060" height="55" alt="image" src="https://github.com/user-attachments/assets/05c11b51-499f-499f-9064-45f951c879e0" />

Configured local username and email:

```
git config user.name "Dhanashree Local"
git config user.email "Local@gmail.com"
```
<img width="1074" height="53" alt="image" src="https://github.com/user-attachments/assets/7f00bfaa-18f3-4f53-affd-200d4220f732" />

Verified using:

```
git config --list
```
<img width="1044" height="53" alt="image" src="https://github.com/user-attachments/assets/2fd9d932-52a1-4ae9-8914-de5d62ba73b6" />



---

## ✅ Task 3: Repository Setup

### 🔹 Created Directory

```
mkdir git-training
cd git-training
git init
```

---

### 🔹 Created Files

```
echo "# Git Training Project" > readme.md
echo "print('Hello Git')" > app.py
```
<img width="1050" height="299" alt="image" src="https://github.com/user-attachments/assets/0bb7c4d5-63dd-4a7d-835c-8e384ecf658f" />

---

### 🔹 Staging & Commit

Checked status:

```
git status
```
<img width="1065" height="227" alt="image" src="https://github.com/user-attachments/assets/6a90b400-d325-43de-91ba-f7efcf793096" />

Staged files:

```
git add .
```
Committed changes:

```
git commit -m "Initial commit: Added readme and app.py"
```
<img width="1054" height="231" alt="image" src="https://github.com/user-attachments/assets/7ebf9a98-4345-4641-b8da-39e6098637dc" />

---

### 🔹 Verified Commit History

```
git log
```
<img width="1063" height="226" alt="image" src="https://github.com/user-attachments/assets/e15e2f03-12fc-4156-b66c-79c44059fd6b" />

---

## ✅ Task 4: Branching & Pull Request

### 🔹 Created Feature Branch

```
git checkout -b feature2
```
<img width="1066" height="52" alt="image" src="https://github.com/user-attachments/assets/c958877b-08ad-4511-884b-0af2901dc54e" />

---

### 🔹 Made Changes in Branch

Updated `app.py`:

```
echo "print('Feature2 change for PR')" >> app.py
```
<img width="1036" height="31" alt="image" src="https://github.com/user-attachments/assets/200642a9-1490-414e-8ff0-edfa045cf0ed" />

---

### 🔹 Staged & Committed Changes

```
git add .
git commit -m "Feature2: Added new print statement for PR demo"
```
<img width="1035" height="263" alt="image" src="https://github.com/user-attachments/assets/414d8f41-e824-4e1e-a8c3-c1b12091269d" />

---

### 🔹 Pushed Feature Branch

```
git push -u origin feature2
```

---<img width="1049" height="330" alt="image" src="https://github.com/user-attachments/assets/5edf7e90-fd97-4057-be02-7c93646b6232" />


### 🔹 Created Pull Request

- Created PR from `feature2` → `main`
- Added proper title and description
- Followed Git best practices:
  - Meaningful branch names
  - Clear commit messages
  - Small focused changes
  - Proper PR description

<img width="1918" height="1032" alt="compare_and_pull" src="https://github.com/user-attachments/assets/7e51ae5f-72bf-4e1e-b688-58cffa62de8b" />
<img width="1918" height="1033" alt="open_pull_request" src="https://github.com/user-attachments/assets/b20cbed6-ebe0-41ec-b1f4-c904d5f5a1b1" />


---

## 🎯 Conclusion

Successfully completed Git practical including:

✔ Git installation  
✔ Global and local configuration  
✔ Repository initialization  
✔ Staging and committing  
✔ Branch creation  
✔ Pull request workflow  

This task helped in understanding real-world Git workflow used in DevOps and software development.

---
