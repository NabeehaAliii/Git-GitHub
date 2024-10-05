# Pre-Commit Hook with Git Bash for Python Projects in VS Code (Windows)

## Problem Statement:

While working on a Python project using **Visual Studio Code** in **Windows**, I faced an issue where pre-commit hooks were not properly running using the **VS Terminal (PowerShell)**. The hook was intended to run `flake8` on all staged Python files to ensure that the code adhered to the specified linting standards before committing. Although the `flake8` linter was installed and configured, the pre-commit hook would not execute correctly, and no errors were flagged during commits even when code contained linting issues.

Moreover, attempts to manually execute the hook failed with errors such as:

- `Cannot spawn .git/hooks/pre-commit: No such file or directory`
- `CommandNotFoundException` when running the hook in PowerShell

## Solution: Using Git Bash for Configuring Pre-Commit Hook

To resolve this issue, I switched from **VS Terminal (PowerShell)** to **Git Bash** to configure and run the pre-commit hook, as it provides better compatibility with Unix-like shell scripts, which is ideal for working with Git hooks.

### Steps to Implement the Solution:

1. **Install Git Bash**:
    - Download and install Git Bash from the official Git website: [Git Download](https://git-scm.com/downloads)
    - After installation, ensure you have Git Bash available in your environment.

2. **Install `flake8`**:
    - Ensure that `flake8` is installed via `pip`:
    ```bash
    pip install flake8
    ```

3. **Navigate to Your Git Repository**:
    - Open Git Bash and navigate to your project folder:
    ```bash
    cd /path/to/your/repository
    ```

4. **Create a Pre-Commit Hook**:
    - In the `.git/hooks` directory, create a new `pre-commit` hook:
    ```bash
    touch .git/hooks/pre-commit
    ```

5. **Make the Pre-Commit Hook Executable**:
    - Ensure the `pre-commit` file is executable:
    ```bash
    chmod +x .git/hooks/pre-commit
    ```

6. **Write the Pre-Commit Script**:
    - Edit the `pre-commit` file using any text editor, such as `vim`, `nano`, or Visual Studio Code, and add the following script:
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
            exit 1  # Abort commit if flake8 fails
        fi
    done

    echo "All Python files passed flake8 checks. Proceeding with commit."
    ```

7. **Test the Pre-Commit Hook**:
    - After configuring the pre-commit hook, you can test it by staging a Python file and attempting a commit:
    ```bash
    git add your_file.py
    git commit -m "Test commit with pre-commit hook"
    ```
    - If there are `flake8` issues, the commit will be aborted.
    - If there are no issues, the commit will succeed.

8. **Manual Flake8 Test**:
    - If the hook doesn't work, try running `flake8` manually to check if the Python files pass the linting rules:
    ```bash
    flake8 your_file.py
    ```

### Additional Notes:

- **Windows Compatibility**: If you're working in Windows using **VS Code** and **PowerShell**, pre-commit hooks may not function as expected due to the way shell scripts are handled in Windows environments. Using **Git Bash** provides a Unix-like shell environment that is better suited for Git hooks.

- **Bypassing the Hook**: If you want to bypass the pre-commit hook temporarily, you can use the `--no-verify` flag when committing:
    ```bash
    git commit -m "Bypass pre-commit" --no-verify
    ```

- **Flake8 Configuration**: You can configure `flake8` settings via a `.flake8` file in your project root directory to adjust linting rules and error thresholds.

## Conclusion:

Switching to **Git Bash** as the terminal for configuring and running Git pre-commit hooks solved the issue I faced while working in **Windows with Visual Studio Code**. Now, every time I commit, `flake8` ensures my Python code meets linting standards, preventing any bad code from being committed.
