# cd — Change Directory

## Purpose

The `cd` command stands for **Change Directory**.

It is used to move from one directory to another within the Linux filesystem. It accepts both absolute paths and relative paths, making it the primary command for filesystem navigation.

---

## Syntax

```bash
cd [directory]
```

---

## Common Variants

| Command                 | Description                                  |
| ----------------------- | -------------------------------------------- |
| `cd /path/to/directory` | Move to a directory using an absolute path   |
| `cd foldername`         | Move to a subdirectory using a relative path |
| `cd ..`                 | Move one level up (parent directory)         |
| `cd ../..`              | Move two levels up                           |
| `cd ~`                  | Move to the user's home directory            |
| `cd`                    | Move to the user's home directory            |
| `cd -`                  | Return to the previous directory             |
| `cd /`                  | Move to the root directory                   |

---


## Examples

### Example 1: Move to a Directory

```bash
cd Documents
```

Current Directory:

```text
/home/aman
```

After Execution:

```text
/home/aman/Documents
```

---

### Example 2: Move to Parent Directory

```bash
cd ..
```

Current Directory:

```text
/home/aman/Documents
```

After Execution:

```text
/home/aman
```

---

### Example 3: Return to Previous Directory

```bash
cd -
```

Output:

```text
/home/aman/Documents
```

This command quickly switches back to the last visited directory.

---

## Common Use Cases

### 1. Navigate to a Project Directory

```bash
cd ~/projects/my_application
```

Used before development, testing, or deployment.

---

### 2. Access System Configuration Files

```bash
cd /etc
```

Used to view or modify system configuration files.

---

### 3. Check System Logs

```bash
cd /var/log
```

Used for troubleshooting and log analysis.

---

### 4. Move to Parent Directory

```bash
cd ..
```

Useful when you accidentally navigate into the wrong folder.

---

### 5. Toggle Between Two Working Directories

```bash
cd -
```

Example:

```bash
cd /var/log
cd /home/aman/projects
cd -
```

Output:

```text
/var/log
```

A very useful productivity feature.

---

### 6. Navigate Within Shell Scripts

```bash
cd /opt/application
./start.sh
```

Used to execute commands relative to a specific location.

---

### 7. Quickly Return to Home Directory

```bash
cd
```

or

```bash
cd ~
```

---

### 8. Access Temporary Files

```bash
cd /tmp
```

Used for testing and temporary storage.

---

### 9. Inspect Running Process Information

```bash
cd /proc
```

Used to explore Linux virtual process files.

---

### 10. Navigate Through Build Directories

```bash
cd build
make
```

Common in software development projects.

---

## Absolute Path vs Relative Path

### Absolute Path

Starts from the root directory (`/`).

```bash
cd /home/aman/Documents
```

Always points to the same location.

---

### Relative Path

Starts from the current directory.

```bash
cd Documents
```

Depends on where you are currently located.

---

## Common Interview Questions

### Q1. What does `cd` stand for?

Change Directory.

---

### Q2. What is the difference between an absolute path and a relative path?

**Absolute Path**

```bash
cd /home/aman/Documents
```

Starts from `/` and is independent of the current directory.

**Relative Path**

```bash
cd Documents
```

Depends on the current working directory.

---

### Q3. What does `cd -` do?

It returns to the previously visited directory.

---

### Q4. What happens when you execute `cd` without arguments?

It moves the user to their home directory.

---

## Related Commands

* pwd
* ls
* find
* tree

---

## Notes

* `cd` is a shell built-in command.
* It does not produce output unless an error occurs.
* One of the most frequently used Linux commands.
* Essential for system administration, development, and troubleshooting.

---

## References

```bash
man cd
help cd
```

---

## Quick Cheat Sheet

```bash
cd              # Home directory
cd ~            # Home directory
cd /            # Root directory
cd ..           # Parent directory
cd ../..        # Two levels up
cd folder       # Enter folder
cd -            # Previous directory
pwd             # Show current location
```
