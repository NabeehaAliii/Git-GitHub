
## Merging Branches in Git Using CLI

Merging in Git allows you to combine the changes from one branch into another. The most common use case is merging feature branches into `main` or `dev`.

### Steps to Merge a Branch:

### 1. **Ensure You’re on the Correct Branch**:
First, make sure you are on the branch where you want to merge the changes **into** (usually `main` or `dev`).

For example, to switch to `main`:
```bash
git switch main
```

### 2. **Pull the Latest Changes** (Optional but recommended):
Before merging, it’s a good idea to make sure your current branch is up-to-date with the remote repository:
```bash
git pull origin main
```

### 3. **Merge the Feature Branch**:
Once you are on the branch where you want to merge changes, use the `git merge` command to merge the other branch into it.

For example, to merge `dev` into `main`:
```bash
git merge dev
```

If you're merging `feature-login` into `dev`, the command would be:
```bash
git merge feature-login
```

### 4. **Handle Merge Conflicts (If Any)**:
If there are any conflicting changes between the two branches, Git will notify you of the conflict and mark the files that need manual intervention. Follow these steps to resolve conflicts:
   - Open the conflicted files and manually resolve the conflicts.
   - After resolving, mark them as resolved:
     ```bash
     git add <file-name>
     ```
   - Complete the merge by committing the resolved changes:
     ```bash
     git commit
     ```

### 5. **Push the Merged Changes to Remote**:
After merging and committing the changes, push them back to the remote repository:
```bash
git push origin main
```

---

### Example Scenario:

If you have a branch named `footer` and you want to merge it into `main`:

1. Switch to `main`:
   ```bash
   git switch main
   ```

2. Pull the latest changes:
   ```bash
   git pull origin main
   ```

3. Merge the `footer` branch into `main`:
   ```bash
   git merge footer
   ```

4. Push the merged changes:
   ```bash
   git push origin main
   ```

---

### Summary of Commands for Merging:
1. **Switch to the branch to merge into**:
   ```bash
   git switch <target-branch>
   ```
2. **Pull the latest changes** (optional but recommended):
   ```bash
   git pull origin <target-branch>
   ```
3. **Merge the source branch into the target branch**:
   ```bash
   git merge <source-branch>
   ```
4. **Push the merged changes to the remote repository**:
   ```bash
   git push origin <target-branch>
   ```
