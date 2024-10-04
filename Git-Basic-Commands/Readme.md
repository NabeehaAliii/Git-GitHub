# Git Basics

## 1. Introduction to Git
**Git** is a distributed version control system that helps track changes in files and coordinate work among multiple people. It allows multiple developers to collaborate on a project without overwriting each other's changes.

---

## 2. Git Commands Cheat Sheet

### a. Initializing a Git Repository
```bash
git init
```
Initializes a new Git repository in your local project.

### b. Cloning a Repository
```bash
git clone <repository-url>
```
Copies an existing Git repository to your local machine.

### c. Checking the Status of the Repository
```bash
git status
```
Shows the status of your working directory and staging area (e.g., which files have been modified or staged).

### d. Staging Files for Commit
```bash
git add <file-name>
```
Stages specific files to be committed. To stage all files, use:
```bash
git add .
```

### e. Committing Changes
```bash
git commit -m "Commit message"
```
Commits staged changes with a brief descriptive message.

### f. Viewing Commit History
```bash
git log
```
Displays the commit history with messages, commit IDs, and authors.

### g. Creating a New Branch
```bash
git branch <branch-name>
```
Creates a new branch for working on a feature or bug fix.

### h. Switching Between Branches
```bash
git checkout <branch-name>
```
Switches to the specified branch.

### i. Merging Branches
```bash
git merge <branch-name>
```
Merges the specified branch into the current branch.

### j. Deleting a Branch
```bash
git branch -d <branch-name>
```
Deletes a branch that is no longer needed.

---

## 3. Working with Remote Repositories

### a. Adding a Remote Repository
```bash
git remote add origin <remote-url>
```
Adds a remote repository (typically hosted on GitHub, GitLab, etc.).

### b. Pushing Changes to Remote
```bash
git push origin <branch-name>
```
Pushes local commits to the specified branch in the remote repository.

### c. Pulling Changes from Remote
```bash
git pull origin <branch-name>
```
Fetches and integrates changes from the remote repository to your local repository.

### d. Cloning a Remote Repository
```bash
git clone <repository-url>
```
Creates a local copy of a remote repository on your machine.

---

## 4. Branching and Merging
- **Branching** allows you to work on new features or fixes independently.
- Use `git branch <branch-name>` to create a branch.
- After making changes, use `git merge <branch-name>` to integrate the feature branch into the main branch.

---

## 5. Undoing Changes

### a. Reverting a File to the Last Commit
```bash
git checkout -- <file-name>
```
Resets a file to its last committed state.

### b. Unstaging a Staged File
```bash
git reset <file-name>
```
Removes the file from the staging area but keeps its changes in your working directory.

### c. Undo the Last Commit (without deleting changes)
```bash
git reset --soft HEAD^
```
Moves the last commit back to the staging area, keeping your changes.

---

## 6. Viewing and Comparing Changes

### a. Viewing Changes in Files
```bash
git diff
```
Shows changes made in your working directory compared to the last commit.

### b. Comparing Branches
```bash
git diff <branch1> <branch2>
```
Shows differences between two branches.

---

## 7. Working with Tags
**Tags** are used to mark specific points in the Git history, typically for releases.

### a. Creating a Tag
```bash
git tag -a v1.0 -m "Version 1.0"
```
Creates a tag with a message for version 1.0.

### b. Pushing Tags to Remote
```bash
git push origin --tags
```
Pushes all local tags to the remote repository.

---

## 8. Git Hooks
Git hooks are scripts that Git executes before or after certain events such as commits. Pre-commit hooks can be used to run tests or format code.

---

## 9. GitHub and Collaboration

### a. Forking a Repository
**Forking** creates a personal copy of someone else’s project. You can make changes and later propose merging them back into the original repository via a **Pull Request**.

### b. Creating a Pull Request (PR)
A **Pull Request** allows you to propose changes you've made in a fork or a branch and request that someone reviews and merges them into the original codebase.

---

## 10. Setting Up a Repository End-to-End (With GitHub Actions)
GitHub Actions automate workflows like Continuous Integration (CI) and Continuous Deployment (CD).

### a. Example Workflow (YAML File for GitHub Actions)
```yaml
name: CI Pipeline

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'
    - run: npm install
    - run: npm test
```
This workflow will run tests automatically whenever code is pushed.

---

## 11. Additional Resources
- **Official Git Documentation**: [https://git-scm.com/doc](https://git-scm.com/doc)
- **GitHub Learning Lab**: [https://lab.github.com/](https://lab.github.com/)
```
