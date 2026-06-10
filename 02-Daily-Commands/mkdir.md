# mkdir — Make Directories

## Purpose

The `mkdir` command stands for **Make Directory**.

It is used to create new directories (folders) in Linux.

Directories help organize files into a structured hierarchy, making file management easier.

`mkdir` can create:

* Single directories
* Multiple directories at once
* Nested directory structures
* Directories with specific permissions

---

## Syntax

```bash
mkdir [options] directory_name
```

---

## Common Options

| Command                            | Description                                |
| ---------------------------------- | ------------------------------------------ |
| `mkdir dir1`                       | Create a single directory                  |
| `mkdir dir1 dir2 dir3`             | Create multiple directories                |
| `mkdir -p parent/child/grandchild` | Create nested directories                  |
| `mkdir -v dir1`                    | Show directory creation details            |
| `mkdir -m 755 dir1`                | Create directory with specific permissions |

---

## Examples

### Example 1: Create a Single Directory

```bash
mkdir project
```

Before:

```text
Documents
Downloads
```

After:

```text
Documents
Downloads
project
```

Creates a new directory named `project`.

---

### Example 2: Create Multiple Directories

```bash
mkdir docs src config
```

Result:

```text
docs/
src/
config/
```

Creates multiple directories in one command.

---

### Example 3: Create Nested Directories

```bash
mkdir -p project/src/python
```

Result:

```text
project/
└── src/
    └── python/
```

The `-p` option automatically creates missing parent directories.

---

### Example 4: Verbose Mode

```bash
mkdir -v backup
```

Output:

```text
mkdir: created directory 'backup'
```

Useful for scripts and automation.

---

### Example 5: Create Directory with Specific Permissions

```bash
mkdir -m 755 website
```

Check:

```bash
ls -ld website
```

Output:

```text
drwxr-xr-x
```

Creates the directory with predefined permissions.

---

## Common Use Cases

### 1. Create a New Project Folder

```bash
mkdir my_project
```

Used before starting development.

---

### 2. Create Project Structure

```bash
mkdir -p project/{src,docs,tests}
```

Result:

```text
project/
├── src/
├── docs/
└── tests/
```

Useful for software projects.

---

### 3. Create Backup Directories

```bash
mkdir backups
```

Store backup files separately.

---

### 4. Create Log Directory

```bash
mkdir /var/log/myapp
```

Used by applications to store logs.

---

### 5. Create Nested Application Structure

```bash
mkdir -p app/config/database
```

Automatically creates all required parent directories.

---

### 6. Create Date-Based Backup Folder

```bash
mkdir backup_$(date +%F)
```

Example:

```text
backup_2026-06-10
```

Useful for daily backups.

---

### 7. Create User Workspace

```bash
mkdir workspace
```

Store development files and projects.

---

### 8. Create Multiple Environment Folders

```bash
mkdir dev test prod
```

Common in deployment environments.

---

## Important Options Explained

### Parent Directory Creation (-p)

Without `-p`:

```bash
mkdir project/src/python
```

Error:

```text
mkdir: cannot create directory
No such file or directory
```

With `-p`:

```bash
mkdir -p project/src/python
```

Success:

```text
project/
└── src/
    └── python/
```

---

### Verbose Mode (-v)

```bash
mkdir -v project
```

Output:

```text
mkdir: created directory 'project'
```

Useful in shell scripts.

---

### Permission Mode (-m)

```bash
mkdir -m 700 private_data
```

Permissions:

```text
drwx------
```

Only the owner can access.

---

## Common Interview Questions

### Q1. What does mkdir stand for?

Make Directory.

---

### Q2. What is the purpose of `-p`?

Creates parent directories automatically.

Example:

```bash
mkdir -p app/config/database
```

---

### Q3. How do you create multiple directories at once?

```bash
mkdir dir1 dir2 dir3
```

---

### Q4. How do you create a directory with specific permissions?

```bash
mkdir -m 755 website
```

---

### Q5. What happens if the directory already exists?

```bash
mkdir project
```

Output:

```text
mkdir: cannot create directory 'project': File exists
```

Use:

```bash
mkdir -p project
```

to avoid the error.

---

## Difference Between mkdir and touch

| Command | Purpose            |
| ------- | ------------------ |
| `mkdir` | Create directories |
| `touch` | Create files       |

Example:

```bash
mkdir project
touch file.txt
```

Result:

```text
project/
file.txt
```

---

## Related Commands

* rmdir
* touch
* cp
* mv
* rm
* tree

---

## Notes

* `mkdir` creates folders, not files.
* Use `-p` for nested directory structures.
* Frequently used in scripting, DevOps, and software development.
* Combine with `tree` to verify directory structure.

---

## References

```bash
man mkdir
info mkdir
```

---

## Quick Cheat Sheet

```bash
mkdir project
mkdir dir1 dir2 dir3
mkdir -p app/config/database
mkdir -v backup
mkdir -m 755 website
mkdir backup_$(date +%F)
ls -ld project
tree
```
