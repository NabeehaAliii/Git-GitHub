# Basics of Git & GitHub

## 1. What is Git?

**Git** is a Distributed Version Control System (VCS) that helps developers track changes in their projects over time. It allows multiple people to work on the same project simultaneously without overwriting each other's work.

### Key Features of Git:
- **Distributed**: Every user has a full copy of the project’s history.
- **Branching & Merging**: Git supports lightweight branches, allowing teams to develop features in parallel.
- **History Tracking**: Every change is tracked, and you can revert to previous versions if necessary.
- **Collaboration**: Git makes it easy for teams to collaborate and manage conflicts in code.
  
---

## 2. What are GitHub, GitLab, and BitBucket?

These platforms offer remote hosting of Git repositories, along with additional features for collaboration and project management.

### a. **GitHub**:
- **Best For**: Open-source projects, collaboration on public and private repositories.
- **Key Features**: GitHub Actions (CI/CD), GitHub Pages, integrations with numerous tools, popular in the open-source community.
- **When to Use**: Use GitHub if your project is public, or if you need an easy-to-use platform with a large community for collaboration.

### b. **GitLab**:
- **Best For**: DevOps pipelines and enterprise use.
- **Key Features**: Built-in CI/CD pipelines, project management tools, GitLab Pages.
- **When to Use**: Use GitLab for enterprise solutions, private repositories, and integrated DevOps workflows.

### c. **BitBucket**:
- **Best For**: Integrating with Jira and other Atlassian tools.
- **Key Features**: Supports both Git and Mercurial, close integration with Jira.
- **When to Use**: If your team uses Jira for project management, BitBucket is a great option for seamless integration.

---

## 3. Difference Between a File System and VCS

### a. **File System**:
A **file system** manages how data is stored and retrieved on a computer. It keeps track of where files are located and how they are accessed.

- **Limitations**:
  - No history tracking: Once a file is overwritten, the previous version is lost.
  - Difficult to collaborate: If multiple people work on the same file, changes can easily be overwritten.
  - Manual backups required to maintain versions.

### b. **Version Control System (VCS)**:
A **VCS** manages changes to documents, code, and other collections of information, storing each change in a repository.

- **Advantages**:
  - **Version History**: VCS keeps track of every modification, enabling easy reversion to any previous state.
  - **Collaboration**: Multiple people can work on the same project without overwriting each other's work.
  - **Branching & Merging**: VCS allows the creation of parallel branches for feature development, which can be merged back into the main project.
  - **Backup**: Every user's copy serves as a backup in distributed VCS systems like Git.

### Example of Key Differences:
- In a **file system**, if you accidentally delete a file, you might lose it forever unless you have a backup. In a **VCS**, you can easily restore any deleted file from the history, even if it's from several versions ago.
- In a **file system**, changes made by multiple collaborators can lead to overwriting files. In a **VCS**, changes are tracked individually, and conflicts can be resolved when merging code.

---

## 4. When to Use Which VCS?

### GitHub:
- **Use for**: Public open-source projects, small to medium teams needing collaboration features, and integrating with popular tools like GitHub Actions.
  
### GitLab:
- **Use for**: DevOps-focused organizations, enterprises with private repositories, and when you need built-in CI/CD pipelines for deployment and testing.

### BitBucket:
- **Use for**: Teams using Atlassian tools like Jira, private codebases, and when you need support for Git and Mercurial.

---

## File System in Git: The Three Stages

In Git, every file in your working directory falls into one of three stages:

### 1. **Untracked**:
   - A file that has not been added to version control is in the **Untracked** state. Git doesn’t track changes for these files until you explicitly add them.

### 2. **Staged**:
   - When a file is **Staged**, it means it has been marked to be included in the next commit. Files are staged by using the `git add` command, which moves them from the Untracked to the Staged state.
   
### 3. **Tracked**:
   - A file that has already been committed to the repository is in the **Tracked** state. Git is now keeping track of its changes. To move files from the **Staged** to **Tracked** state, you need to commit them.

---

### Git Commands for Moving Between Stages

#### a. Moving from **Untracked** to **Staged**:
- Use `git add <filename>` to add a specific file to the staging area:
  ```bash
  git add <filename>
  ```

#### b. Moving All Untracked Files to Staged:
- Use `git add .` to add all untracked files in the current directory to the staging area:
  ```bash
  git add .
  ```

#### c. Moving from **Staged** to **Tracked**:
- Once files are staged, use `git commit` to commit them, moving them to the tracked state:
  ```bash
  git commit -m "Added testing files"
  ```

---

### Color Representation in Git
When you run `git status`, you will see files represented in different colors:
- **Red**: Untracked files that are not yet staged.
- **Green**: Files that are staged and ready to be committed.

---

### Undoing Staged Changes: Moving from **Staged** to **Untracked**
If you mistakenly added a file to the staging area and want to unstage it (but not delete the file), use the `git rm --cached` command:
```bash
git rm --cached <filename>
```
This command removes the file from the staging area but keeps it in your working directory.

---

### Removing and Recovering Files

#### a. Removing a Tracked File
If you want to delete a file from your working directory, simply use the `rm` command:
```bash
rm Testing.py
```
The file will be removed from your file system, and Git will mark it as deleted.

#### b. Recovering a Deleted File
If you accidentally delete a file, you can recover it using Git. First, check the file status with:
```bash
git status
```
You’ll see the deleted file marked as missing (in red). To recover it, use:
```bash
git restore Testing.py
```
This command restores the deleted file back to its last committed state.

---

## Summary of Commands

1. **Add a file to staging**: 
   ```bash
   git add <filename>
   ```
2. **Add all untracked files to staging**: 
   ```bash
   git add .
   ```
3. **Commit staged files**: 
   ```bash
   git commit -m "Commit message"
   ```
4. **Unstage a file**: 
   ```bash
   git rm --cached <filename>
   ```
5. **Remove a file**: 
   ```bash
   rm <filename>
   ```
6. **Restore a deleted file**: 
   ```bash
   git restore <filename>
   ```


This section explains the three stages of files in Git, how to move files between these stages, and some helpful commands for managing and recovering files. Let me know if you want to add anything else!
---

# **Pushing Changes to GitHub Using Personal Access Token (PAC)**

### 1. Create a GitHub Repository:
First, create a repository on GitHub. You can either choose a public or private repository depending on your project requirements. In this case, the repository URL is:
```
https://github.com/NabeehaAliii/GIT-GITHUB-FOR-DEVOPS-WORKSHOP.git
```

---

### 2. Link Your Local Repository to GitHub:
If you already have a local Git repository and want to link it to the remote GitHub repository, use the following steps.

#### a. **Adding the Remote**:
Use the `git remote add origin` command to link the remote GitHub repository to your local repository:
```bash
git remote add origin https://github.com/NabeehaAliii/GIT-GITHUB-FOR-DEVOPS-WORKSHOP.git
```

#### b. **Check Remote Configuration**:
After adding the remote, verify the remote URLs using:
```bash
git remote -v
```
This should show both the `fetch` and `push` URLs for the remote.

---

### 3. Dealing with Default Branch Differences:
By default, the branch in your **local Git repository** might be named `master`, whereas the branch in your GitHub repository is named `main`. 

#### a. **Set URL with PAC**:
To use a **Personal Access Token (PAC)** for authentication when pushing to GitHub, set the remote URL with your PAC included in it. Use the following command (replace `<your-pac>` with your actual PAC):
```bash
git remote set-url origin http://<your-pac>@github.com/NabeehaAliii/GIT-GITHUB-FOR-DEVOPS-WORKSHOP.git
```

For example:
```bash
git remote set-url origin http://@github.com/NabeehaAliii/GIT-GITHUB-FOR-DEVOPS-WORKSHOP.git
```

Check the updated remote configuration again:
```bash
git remote -v
```

---

### 4. Push Changes to GitHub:
Once the remote is set up correctly and you're ready to push your changes from your local branch to the `main` branch on GitHub, use the following command:
```bash
git push origin main
```

This command pushes the changes from your local repository to the `main` branch on the remote GitHub repository.

---

### Summary of Commands:
1. **Add a remote**:
   ```bash
   git remote add origin <repository-url>
   ```
2. **Set the remote URL with PAC**:
   ```bash
   git remote set-url origin http://<your-pac>@github.com/<username>/<repository>.git
   ```
3. **Check the remote configuration**:
   ```bash
   git remote -v
   ```
4. **Push changes to GitHub**:
   ```bash
   git push origin main
   ```
---

This section explains how to connect your local repository to GitHub, use a PAC for authentication, and push changes to the remote repository. Let me know if you need any further details!
---

## How to Generate a Personal Access Token (PAC) for GitHub

In GitHub, a **Personal Access Token (PAC)** can be used to authenticate access to your repositories, replacing your GitHub password when working with Git over HTTPS.

### Steps to Generate a Personal Access Token:

1. **Go to GitHub Settings**:
   - Log in to your GitHub account and navigate to your **Settings** by clicking on your profile picture at the top-right corner.
   
2. **Go to Developer Settings**:
   - Scroll down to find **Developer Settings** on the left sidebar, and click it.

3. **Generate a New Token**:
   - In the **Personal access tokens** section, click on **Tokens (classic)**, and then click on the **Generate new token** button.

4. **Add Note and Expiration**:
   - Add a note describing the token’s purpose (e.g., "Git for DevOps Workshop").
   - Set an expiration period (e.g., 30 days, 90 days, or custom).

5. **Select Scopes**:
   - Choose the permissions or **scopes** you want to grant the token. For basic repository access, select:
     - `repo`: Full control of private repositories.
     - `workflow`: For GitHub Actions.
     - `admin:repo_hook`: To manage webhooks and services.
   - Additional scopes can be added depending on your requirements.

6. **Generate Token**:
   - Click **Generate token**. **IMPORTANT**: You will only see this token once! Copy it immediately and store it in a secure place.

7. **Use the Token**:
   - Replace your GitHub password with this token when prompted for authentication during `git push` or `git pull` commands.
   - Example:
     ```bash
     git remote set-url origin http://<your-token>@github.com/<username>/<repository>.git
     ```

### Example:
Here’s how a token looks (ensure you don't share your token publicly):
```
ghp_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```
---

This section outlines the process of generating a PAC and how to use it in Git operations.
---

## 5. Summary
- **Git** is a distributed version control system that helps teams track and manage changes in projects.
- **GitHub, GitLab, and BitBucket** are platforms for hosting Git repositories with additional collaboration and CI/CD features.
- A **file system** is limited to basic storage, while a **VCS** provides robust version tracking, history, and collaboration features.

For more information, you can visit:
- **Git Documentation**: [https://git-scm.com/doc](https://git-scm.com/doc)
- **GitHub Learning Lab**: [https://lab.github.com/](https://lab.github.com/)
