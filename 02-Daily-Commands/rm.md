# rm — Remove Files and Directories

## Purpose

The `rm` command stands for **Remove**.

It is used to permanently delete files and directories from the Linux filesystem.

Unlike Windows or graphical file managers, files deleted using `rm` are usually **not moved to a Recycle Bin or Trash**. Once removed, recovery can be difficult or impossible without backups.

Because of its destructive nature, `rm` should be used carefully, especially with recursive and force options.

---

## Syntax

```bash
rm [options] file_or_directory
```

---

## Common Options

| Option             | Description                                          |
| ------------------ | ---------------------------------------------------- |
| `rm file`          | Delete a single file                                 |
| `rm -r directory`  | Delete a directory and its contents recursively      |
| `rm -f file`       | Force deletion without confirmation                  |
| `rm -rf directory` | Forcefully delete directory and contents recursively |
| `rm -i file`       | Ask for confirmation before deleting                 |
| `rm -v file`       | Show detailed deletion information                   |
| `rm *.log`         | Delete all files matching a pattern                  |

---

## Examples

### Example 1: Delete a Single File

```bash
rm report.txt
```

Before:

```text
report.txt
```

After:

```text
File deleted
```

The file is permanently removed.

---

### Example 2: Delete a Directory

```bash
rm -r project_backup
```

Before:

```text
project_backup/
```

After:

```text
Directory deleted
```

The directory and all files inside it are removed.

---

### Example 3: Interactive Deletion

```bash
rm -i config.conf
```

Output:

```text
rm: remove regular file 'config.conf'?
```

The command waits for user confirmation.

---

### Example 4: Verbose Deletion

```bash
rm -v old.log
```

Output:

```text
removed 'old.log'
```

Useful for scripts and troubleshooting.

---

## Common Use Cases

### 1. Remove Temporary Files

```bash
rm /tmp/tempfile.txt
```

Delete temporary files that are no longer needed.

---

### 2. Clean Old Log Files

```bash
rm *.log
```

Free disk space by removing old log files.

---

### 3. Remove Build Artifacts

```bash
rm -rf build/
```

Common after software compilation.

---

### 4. Delete Cache Files

```bash
rm -rf ~/.cache/*
```

Used to clean application cache data.

---

### 5. Remove Backup Files

```bash
rm *.bak
```

Delete outdated backup copies.

---

### 6. Delete Files Found by find

```bash
find . -name "*.tmp" -exec rm {} \;
```

Remove all temporary files from the current directory tree.

---

### 7. Interactive Bulk Deletion

```bash
rm -i *.txt
```

Confirms each file before deletion.

---

### 8. Remove Empty Test Directories

```bash
rm -r test_environment/
```

Delete development or testing folders.

---

### 9. Remove Multiple Files

```bash
rm file1.txt file2.txt file3.txt
```

Delete several files at once.

---

### 10. Force Delete Read-Only Files

```bash
rm -f readonly.txt
```

Deletes files without prompting.

---

## Important Options Explained

### Recursive Delete (-r)

```bash
rm -r directory_name
```

Deletes:

* Directory
* Subdirectories
* All files inside

Required when removing directories.

---

### Force Delete (-f)

```bash
rm -f file.txt
```

* No confirmation
* Ignores non-existent files
* Deletes read-only files

Use carefully.

---

### Recursive + Force (-rf)

```bash
rm -rf directory_name
```

Deletes everything immediately.

This is one of the most powerful and dangerous Linux commands.

---

### Interactive Mode (-i)

```bash
rm -i important.txt
```

Prompts before deletion.

Recommended for important files.

---

## ⚠️ Dangerous Commands

Never run these commands:

```bash
rm -rf /
```

```bash
rm -rf /*
```

```bash
rm -rf ~
```

These commands can delete critical system files or your entire home directory.

Modern Linux distributions often provide protections, but you should never rely on them.

---

## Difference Between rm and rmdir

| Command | Purpose                       |
| ------- | ----------------------------- |
| `rm`    | Delete files and directories  |
| `rmdir` | Delete only empty directories |

Example:

```bash
rmdir empty_folder
```

If the directory contains files, `rmdir` will fail.

---

## Common Interview Questions

### Q1. What is the difference between rm and rmdir?

* `rm` removes files and directories.
* `rmdir` removes only empty directories.

---

### Q2. What does `rm -rf` mean?

* `-r` = Recursive
* `-f` = Force

Together they delete directories and all contents without confirmation.

---

### Q3. Can deleted files be recovered?

Usually not easily.

Recovery may require:

* Backups
* Filesystem recovery tools
* Professional recovery software

---

### Q4. Why should `rm -rf` be used carefully?

Because it permanently removes files without asking for confirmation.

Mistakes can result in significant data loss.

---

### Q5. How can you safely delete files?

```bash
rm -i filename
```

This asks for confirmation before deletion.

---

## Related Commands

* rmdir
* find
* cp
* mv
* shred

---

## Notes

* Always verify file paths before deletion.
* Use `rm -i` for important files.
* Maintain backups before running large deletion operations.
* Avoid running `rm -rf` as the root user unless absolutely necessary.
* Double-check wildcard usage such as `*.log` before execution.

---

## References

```bash
man rm
info rm
```

---

## Quick Cheat Sheet

```bash
rm file.txt
rm -i file.txt
rm -v file.txt
rm -f file.txt
rm -r directory/
rm -rf directory/
rm *.log
find . -name "*.tmp" -exec rm {} \;
```
