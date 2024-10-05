# **GitHub Repository: Clone, Fork, and Sync**

## Overview:
This guide demonstrates how to effectively clone a GitHub repository, fork it for independent development, and keep the fork synced with the original repository. It also covers how to pull changes from GitHub to your local machine to stay updated with the latest code.

---

## 1. Cloning and Forking Repositories:

### a. **Clone a Repository (GitHub to Local)**:
Cloning allows you to copy a GitHub repository to your local machine for development.

#### Command:
```bash
git clone https://github.com/NabeehaAliii/LondheShubham153_ForkTesting.git
```
This command clones the repository from GitHub to your local system, where you can make changes and commit updates.

---

### b. **Fork a Repository (GitHub to Fork)**:
Forking a repository allows you to create your own copy of someone else’s repository on your GitHub account. You can work independently on the forked repo.

- Once you’ve forked a repository, it will show up under **your GitHub account**. You can then clone this fork to your local system just like any other repository.

---

### c. **Syncing a Fork**:
After you’ve forked a repository and made changes, it’s important to keep your fork in sync with the original repository (upstream) to avoid conflicts.

#### Steps to Sync Fork:
1. **Add the Original Repository (Upstream) as Remote**:
   ```bash
   git remote add upstream https://github.com/original-owner/original-repo.git
   ```

2. **Fetch Latest Changes from Upstream**:
   ```bash
   git fetch upstream
   ```

3. **Merge Upstream Changes into Your Fork**:
   ```bash
   git merge upstream/main
   ```

4. **Push Changes to Your Fork**:
   ```bash
   git push origin main
   ```

---

## 2. Pulling Changes from GitHub to Local:

### a. **Pull (Sync Changes from GitHub to Local)**:
To keep your local copy updated with changes from the GitHub repository, you need to **pull** the latest changes.

#### Command:
```bash
git pull origin main
```
This command fetches and merges changes from the `main` branch of the remote GitHub repository into your local repository.

---

## 3. Additional Commands:

### a. **View the List of Remotes**:
To check which remotes are linked to your repository:
```bash
git remote -v
```

### b. **Push Changes from Local to GitHub**:
Once you’ve made changes locally, you can push them to the remote GitHub repository.
```bash
git push origin main
```

---

## Summary of Key Commands:
1. **Clone a repository**: 
   ```bash
   git clone <repository-url>
   ```
2. **Fork and Sync a repository**:
   - Add upstream: `git remote add upstream <upstream-repo-url>`
   - Fetch upstream: `git fetch upstream`
   - Merge: `git merge upstream/main`
3. **Pull latest changes**: 
   ```bash
   git pull origin main
   ```

For more information, visit [GitHub Docs](https://docs.github.com/).
---

## Author:
**Nabeeha Ali**  
Feel free to fork this repository and contribute!
```

This **README.md** file covers the essential commands and steps for cloning, forking, and pulling changes from a GitHub repository. Let me know if you'd like any additional customization!
