# Terminal & CLI Cheat Sheet

Command Line Interface (CLI) navigation, file manipulation, and system utilities.

## Safe & Common Commands

### 1. Navigation
```bash
# Print working directory path
pwd

# List directory contents (with details and hidden files)
ls -la

# Change directory
cd path/to/folder

# Go back to the parent directory
cd ..
```

### 2. File and Folder Management
```bash
# Create a new directory
mkdir new-project

# Create a blank file
touch index.html

# Copy a file
cp source.js destination.js

# Move or rename a file
mv old-name.js new-name.js
```

---

## ⚠️ Destructive Commands (Use with Caution)

> [!CAUTION]
> File deletions in terminal bypass the recycle bin / trash can. They are permanent.

### 1. Forceful and Recursive Deletions
```bash
# Deletes a file permanently without prompt
rm filename.txt

# Recursively deletes a directory and all of its contents without prompting
rm -rf directory-name
```
*Why it's dangerous:* Running `rm -rf` on the wrong folder (or using wildcards like `rm -rf *` in the wrong place) can wipe out your entire project directory or operating system. Always double-check your current directory using `pwd` before running this command.

---

## Authoritative Documentation
- [Linux Command Line Basics (Ubuntu Guide)](https://ubuntu.com/tutorials/command-line-for-beginners)
- [Microsoft PowerShell Documentation](https://learn.microsoft.com/en-us/powershell/)
