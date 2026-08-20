# GitHub

---

## GitHub or AWS

| Analogy | Explanation |
|---------|-------------|
| User name, Password and One time Code | Home Address |
| Repo Name | Floor and Room Number |

**Email:** goodszenith5@gmail.com

---

## Define GitHub

GitHub is a **cloud-based repository hosting platform** that uses **Git** (the version control tool) to manage and collaborate on code.

It is a **distributed decentralized cloud based repository** which is used to maintain the source code/automation framework/CRS document/build versions in one place.

> **Note:** Git = Version Control Tool | GitHub = Cloud Platform that hosts Git repositories

---

## Advantages

1. Since it is cloud based repository maintenance team is not required.
2. Since it is cloud based repository we can access the repository via internet from any place.
3. Cloud means pay for what you use (GitHub Free tier available with 10 GB storage; paid plans for extra features).
4. Cloud means contributors can access the code from remote places.
5. It provides a platform for File sharing among the team members.
6. It provides way to solve conflicts in code.
7. Jenkins also gets the new build from github.
8. Scale up/scale down is easy.
9. It also provides history of changes made in the framework.
10. No initial investment needed for storage. "GitHub Free provides up to 10 GB of Git Large File Storage (Git LFS) storage and 10 GB of bandwidth, subject to GitHub's applicable terms and limits".
11. It provides a way to review the automation framework.

---

## Softwares in GitHub

### GitHub

It is a cloud based repository which can be accessed via [https://github.com](https://github.com)

We should create an account in github.com

### Git

It is a **version control tool** that tracks code changes locally and communicates with remote repositories like GitHub. It is the place where we write our commands.

```
laptop Codes <---> GitHub Repository
```

**Two components:**

1. **GitClient:** It should be installed in our local system. This takes care of the local repository.
   - Ex: Git is available in Eclipse.

2. **GitBash:** It should be installed in local disk. This is used to perform all operations via command line.

---

## Usage by Different Roles

| Role | Usage |
|------|-------|
| **Developer** | Developers use GitHub to maintain their source code |
| **Automation Engineer** | To maintain automation framework |
| **DevOps** | To maintain build versions |
| **Manual Testers** | To maintain CRS (Customer Requirement Specification) document |

---

## Why GitHub is a Decentralized Repository?

When the code is to be pushed to global repository it initially creates a **local repository** and stores the code first and verifies if the code is working fine or not. Only then it is pushed to the global repository.

```
Local Repository (verify code) --> Global Repository (push after verification)
```

---

---

# Git Commands and Workflow

---

## Git Flow Overview

```
Working Directory
      ↓ git add
Staging Area
      ↓ git commit
Local Repository (.git)
      ↓ git push
Remote Repository (GitHub)
```

---

## Downloading Code (Downstream: GitHub → Local)

### 1. Git Clone (First Time - Entire Framework)

```bash
git clone <repository-url>
```

- Downloads the **complete project** with full history
- Example: Remote Repository = 16 GB → You get all 16 GB
- Use this only **once** when starting on a project

```bash
git clone https://github.com/ToushifAnsari786/Java_Script.git
```

---

### 2. Git Pull (After Clone - Only Updates)

```bash
git pull
```

- Downloads **only the new changes** (not the entire project again)
- Example: If someone added 1 GB of new code → You download only that 1 GB
- Use this **every time** before starting your work

```bash
git pull origin main
git pull origin master
```

---

### 3. Git Status (Check What Changed)

```bash
git status
```

- Shows modified files, new files, staged files
- Shows current branch status
- Use **before add** and **after add** to verify

---

## Uploading Code (Upstream: Local → GitHub)

### Step 1: Initialize Git (One Time for New Project)

```bash
git init
```

- Creates a hidden `.git` folder inside your project
- This folder is your **local repository**

```
MyProject/
├── tests/
├── pages/
├── package.json
└── .git/        ← created by git init
```

---

### Step 2: Configure Username & Email ⚡ Only First Time

```bash
git config --global user.email "goodszenith5@gmail.com"
git config --global user.name "ToushifAnsari786"
git config --global --list
```

- Identifies **who** made the commit
- Verify with: `git config --global --list`

---

### Step 3: Connect to Remote Repository ⚡ Only First Time

```bash
git remote add origin https://github.com/ToushifAnsari786/Java_Script.git
git remote -v
```

- Links your local repo to GitHub
- `origin` = name for the remote repository
- Verify with: `git remote -v`

---

### Step 4: Stage Changes (git add)

```bash
git add .                    # Add ALL changes
git add filename.js          # Add specific file
git add tests/               # Add specific folder
```

- Moves changes from **Working Directory → Staging Area**
- Binds selected files into a single package ready for commit

---

### Step 5: Commit Changes (git commit)

```bash
git commit -m "Added login automation test"
```

- Moves staged changes from **Staging Area → Local Repository (.git)**
- The message describes what you changed

---

### Step 6: Push to GitHub (git push)

```bash
git push -u origin master
git push -u origin main
```

- Moves committed code from **Local Repository (.git) → GitHub Remote Repository**
- `-u` sets upstream tracking (after first push, just use `git push`)

---

## Quick Reference Card

| # | Command | What It Does |
|---|---------|--------------|
| 1 | `git clone <url>` | Download entire project (first time only) |
| 2 | `git pull` | Download only new updates |
| 3 | `git status` | Check what files changed |
| 4 | `git init` | Initialize new local repository |
| 5 | `git config --global user.email "email"` | Set email ⚡ First time only |
| 6 | `git config --global user.name "name"` | Set username ⚡ First time only |
| 7 | `git remote add origin <url>` | Connect to GitHub ⚡ First time only |
| 8 | `git add .` | Stage all changes |
| 9 | `git commit -m "message"` | Save to local repository |
| 10 | `git push -u origin master` | Upload to GitHub |

---

## Workflow: New Project (Upload to GitHub)

```bash
git init
git config --global user.email "goodszenith5@gmail.com"    # ⚡ First time
git config --global user.name "ToushifAnsari786"            # ⚡ First time
git remote add origin <repository-url>                      # ⚡ First time
git add .
git commit -m "Initial commit"
git push -u origin main
```

---

## Workflow: Existing Project (Already on GitHub)

```bash
git clone <repository-url>       # Step 1: Download project (first time)
cd project-name                  # Step 2: Enter project folder
git status                       # Step 3: Check status
git pull                         # Step 4: Get latest changes
# ... make your changes ...      # Step 5: Edit files
git status                       # Step 6: Verify changes
git add .                        # Step 7: Stage changes
git commit -m "Updated tests"    # Step 8: Commit
git push                         # Step 9: Push to GitHub
```

---

## Upstream vs Downstream

| Direction | Flow | Commands |
|-----------|------|----------|
| **Downstream** ⬇️ | GitHub → Local System | `git clone`, `git pull` |
| **Upstream** ⬆️ | Local System → GitHub | `git push` |

---

## Create a New Branch

A branch is a separate line of development in Git. It allows you to work on a feature, bug fix, or experiment without affecting the main branch.

```bash
git checkout -b Salman_ansari
```

### Definition
- `git checkout` = switch to a branch
- `-b` = create a new branch
- `Salman_ansari` = name of the new branch

This command creates a new branch named `Salman_ansari` and immediately switches to it.

---