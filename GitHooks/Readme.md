# Git Hooks and Pre-Commit Hooks for DevOps Beginners

## 1. What are Git Hooks?

**Git Hooks** are scripts that Git automatically executes before or after certain actions. They allow you to automate tasks such as linting, testing, or enforcing policies before commits or pushes. There are two main types of Git hooks:
- **Client-Side Hooks**: These run on operations such as commit, merge, or checkout. Examples include pre-commit, commit-msg, and post-commit.
- **Server-Side Hooks**: These run on Git server actions such as receiving pushed commits or validating incoming changes.

### a. **Pre-Commit Hook**:
The **pre-commit** hook is triggered before a commit is made. It's often used to check code quality, format code, or perform security checks (e.g., ensuring no sensitive data like passwords or API keys are committed).

---

## 2. Viewing Hidden Hook Files

To view the hidden `.git` directory where Git hooks are stored, use the following commands based on your operating system:

- **For Windows**:
  ```bash
  Get-ChildItem -Force
  ```

- **For Linux/macOS**:
  ```bash
  ls -a
  ```

This will show the `.git/hooks` directory, which contains sample hook scripts like `pre-commit.sample`.

---

## 3. Why Use Git Hooks?

Hooks are essential in DevOps workflows as they:
- Ensure code quality by automating checks (e.g., running linters, unit tests).
- Enforce coding standards and prevent poorly formatted or insecure code from being committed.
- Automate repetitive tasks like code formatting or notifying a team about new commits.

By automating these tasks with hooks, developers can focus more on feature development rather than manually running checks.

---

## **Note**: Using Git Bash Instead of Windows Terminal

While you can configure hooks on both Git Bash and Windows Terminal, **Git Bash** is often the more reliable environment when working with hooks, especially in Windows. Windows Terminal may cause issues with permission settings or executable files. So, we highly recommend using **Git Bash** to avoid any complications when creating or testing hooks.

---

## 4. Demo: Setting up a Pre-Commit Hook with Flake8

In this demo, we'll set up a **pre-commit hook** to ensure all Python files in the repository meet quality standards using **Flake8**.

### Step 1: Create a Demo Python File
We created a demo Python file (`demoForHooks.py`) that contains a basic function.

```python
def my_function():
    a = 5
    b = 6
    c = 7
    return d
```

### Step 2: Install Flake8 for Code Quality Checks
**Flake8** is a Python tool that checks for style guide enforcement (PEP8) and common issues like unused variables and imports.

To install it, run:
```bash
pip install flake8
```
check for flake8 working, run:
```bash
flake8 demoForHooks.py
```
<img width="960" alt="Hooks_flake8" src="https://github.com/user-attachments/assets/ca032cac-4ad2-4b7d-b3d0-9c99c91df84d">

### Step 3: Configure the Pre-Commit Hook

1. Navigate to the `.git/hooks` directory:
   ```bash
   cd .git/hooks
   ```

2. Create or modify the `pre-commit` file:
   ```bash
   nano pre-commit
   ```

3. Add the following script to the `pre-commit` file:

```bash
#!/bin/bash
echo "Running pre-commit hook to check Python files..."

# Get all staged Python files
files=$(git diff --cached --name-only --diff-filter=ACM | grep '\.py$')

# If no Python files are staged, exit
if [ -z "$files" ]; then
  echo "No Python files to check."
  exit 0
fi

# Run flake8 on each staged Python file
for file in $files; do
  echo "Checking $file with flake8..."
  flake8 "$file"
  if [ $? -ne 0 ]; then
    echo "flake8 failed on $file. Commit aborted."
    exit 1 # Exit with error to abort commit
  fi
done

echo "All Python files passed flake8 checks. Proceeding with commit."
```

4. Make the pre-commit script executable:
   ```bash
   chmod +x pre-commit
   ```

---

## 5. Adding a Hook to Detect Sensitive Data

To prevent sensitive data (e.g., passwords, secret keys, or API keys) from being committed, we can add an additional check to the **pre-commit hook**.

Modify the `pre-commit` file to include the following:

```bash
# Check for sensitive data in staged files
if git grep -q "password\|secret_key\|API_key" $(git diff --cached --name-only); then
  echo "Sensitive data found in staged files. Please remove it before committing."
  exit 1 # Abort commit if sensitive data is found
fi
```

### Updated Pre-Commit Hook with Sensitive Data Check

```bash
#!/bin/bash
echo "Running pre-commit hook to check Python files and sensitive data..."

# Get all staged Python files
files=$(git diff --cached --name-only --diff-filter=ACM | grep '\.py$')

# If no Python files are staged, exit
if [ -z "$files" ]; then
  echo "No Python files to check."
  exit 0
fi

# Run flake8 on each staged Python file
for file in $files; do
  echo "Checking $file with flake8..."
  flake8 "$file"
  if [ $? -ne 0 ]; then
    echo "flake8 failed on $file. Commit aborted."
    exit 1 # Exit with error to abort commit
  fi
done

echo "All Python files passed flake8 checks. Proceeding with commit."

# Check for sensitive data in staged files
if git grep -q "password\|secret_key\|API_key" $(git diff --cached --name-only); then
  echo "Sensitive data found in staged files. Please remove it before committing."
  exit 1 # Abort commit if sensitive data is found
fi
```

<img width="960" alt="pre-commit_hooks" src="https://github.com/user-attachments/assets/e1320324-3564-4095-8195-4e760eaf5b5e">


---

## 6. Running the Pre-Commit Hook

Once the pre-commit hook is set up, every time you try to commit, the hook will run **Flake8** to check all staged Python files and ensure no sensitive data is committed.

### Example:
```bash
git commit -m "Test commit with pre-commit hook"
```

If there are any issues (e.g., Flake8 violations or sensitive data found), the pre-commit hook will output errors and abort the commit:

<img width="960" alt="sensitive_hook" src="https://github.com/user-attachments/assets/0f839054-6626-4b6f-9105-378c809ec8b2">

---

## Summary of Key Commands

1. **Install Flake8**:
   ```bash
   pip install flake8
   ```

2. **View Hidden Files**:
   - Windows:
     ```bash
     Get-ChildItem -Force
     ```
   - Linux/macOS:
     ```bash
     ls -a
     ```

3. **Create and Edit Pre-Commit Hook**:
   ```bash
   cd .git/hooks
   nano pre-commit
   ```

4. **Make the Pre-Commit Hook Executable**:
   ```bash
   chmod +x pre-commit
   ```

5. **Detect Sensitive Data**:
   Ensure your pre-commit hook checks for sensitive data like `password`, `secret_key`, or `API_key`.

---

For more details on Git Hooks, you can refer to the [Git Documentation on Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks).
```
