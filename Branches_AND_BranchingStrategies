# Branching in Git: Branching Strategy

## 1. What are `main` and `master` branches?

- **Main**: The **main** branch is the default branch in GitHub repositories as of October 2020. It typically contains the **production-ready code**. It is where all feature branches ultimately get merged.
  
- **Master**: Previously, the default branch was called **master**. Many older repositories still use `master`, but moving forward, new repositories use `main`. The two terms can be used interchangeably depending on the repository configuration, but `main` is now the preferred name.

---

## 2. Working with Branches

### a. **What is a Branch?**
- A branch in Git is simply a lightweight movable pointer to a commit. Every branch in Git maintains its own copy of the codebase, which allows you to work on different features or bug fixes in isolation without affecting the main codebase.
  
- **Branching** allows you to work on multiple parts of a project simultaneously. Each branch represents a separate line of development.

### b. **Creating and Switching Between Branches**

#### Create a new branch:
```bash
git branch <new-branch-name>
```
This creates a new branch, but you will stay on your current branch until you switch.

#### Switch to the new branch:
```bash
git switch <branch-name>
```
Switches to the specified branch. For example:
```bash
git switch dev
```

#### Note: Difference Between `git checkout` and `git switch`:
- **`git checkout`**: Historically used for switching branches and creating new ones. It can also be used for checking out files or commits, making it more versatile but sometimes confusing.
- **`git switch`**: Introduced as a more intuitive way to switch between branches. It is explicitly used for branch switching and creating branches.

---

## 3. Making Copies of a Repository: Is It Called Branching?
- In Git, branching is **not a copy of the entire repository**; rather, it’s a pointer to a specific commit, allowing multiple versions of the codebase to exist simultaneously.
- Branches are more like separate versions of the same code rather than complete copies.

---

## 4. Branching Strategy

In collaborative development, different branches are used for different purposes:

### a. **Main Branch**:
   - The **main** branch (previously known as master) contains the best and stable code. This is the production-ready branch that holds the final version of the software.

### b. **Staging Branch**:
   - Used for **testing** and **user testing**. Code from the development branch is merged here to prepare for production.

### c. **Development Branch (Dev)**:
   - This branch is where active development takes place. Developers commit code here before it is tested.
  
   - When multiple developers are working on the same project, it’s a good practice to create **feature branches** off of the `dev` branch for specific tasks, such as:
     - `feature-login`
     - `feature-logout`
  
     After completing the feature, developers merge these feature branches back into the `dev` branch.

### d. **Commit and Head**
   - The **latest commit** in any branch is referred to as **HEAD**. You can check recent commits using:
     ```bash
     git log --oneline
     ```

---

## 5. Merging Branches

### a. Scenario:
You made 3 to 4 commits on the **main** branch, then created a new branch called `dev` and made 1 commit there. To merge your work, you need to pull the latest changes from `main` into `dev` to synchronize both.

#### Steps:
1. Switch to the `dev` branch:
   ```bash
   git switch dev
   ```
2. Pull the latest changes from `main` into `dev`:
   ```bash
   git pull origin main
   ```
   This command fetches and merges the changes from the `main` branch into your `dev` branch.

3. Resolve any merge conflicts (if applicable) and commit the merged changes.

---

## 6. Remote Branches

### a. **Creating a Remote Branch**:
Once you’ve created a new branch locally, you can push it to the remote repository (GitHub) for others to access.

#### Example:
```bash
git push origin <new-branch-name>
```

### b. **Fetching Remote Changes**:
If a new branch is created in the remote repository (e.g., on GitHub), you can **fetch** it to see the latest updates without merging them into your local branches.

#### Command:
```bash
git fetch
```

---

## 7. Difference Between `git fetch` and `git pull` (Simplified)

### a. **`git fetch`**:
- Fetches the latest changes from the remote repository but does **not** merge them into your current branch.
- Use this to see changes before merging them manually.

### b. **`git pull`**:
- Fetches the latest changes **and** automatically merges them into your current branch.
- Use this to stay updated with the latest changes from the remote branch.

---

## Summary of Commands:

1. **Create a branch**:
   ```bash
   git branch <new-branch-name>
   ```
2. **Switch to a branch**:
   ```bash
   git switch <branch-name>
   ```
3. **Fetch changes from a remote branch**:
   ```bash
   git fetch
   ```
4. **Pull and merge changes from a remote branch**:
   ```bash
   git pull origin <branch-name>
   ```
5. **Push a new branch to a remote repository**:
   ```bash
   git push origin <new-branch-name>
   ```
---
