# cp — Copy Files and Directories

## Purpose

The `cp` command stands for **Copy**.

It is used to copy files and directories from one location to another. The original file remains unchanged, and a duplicate is created at the destination.

The `cp` command supports recursive directory copying, preserving file attributes, interactive confirmation before overwriting, and archive mode for backups.

---

## Syntax

```bash
cp [options] source destination
```

---

## Common Options

| Option                         | Description                                     |
| ------------------------------ | ----------------------------------------------- |
| `cp source destination`        | Copy a single file                              |
| `cp -r source_dir destination` | Copy a directory recursively                    |
| `cp -p file destination`       | Preserve permissions, ownership, and timestamps |
| `cp -i file destination`       | Ask before overwriting an existing file         |
| `cp -v file destination`       | Show detailed copy operation                    |
| `cp -n file destination`       | Never overwrite existing files                  |
| `cp -u file destination`       | Copy only if source is newer                    |
| `cp -a source destination`     | Archive mode (preserve all attributes)          |

---

## Examples

### Example 1: Copy a File

```bash
cp report.txt backup_report.txt
```

Before:

```text
report.txt
```

After:

```text
report.txt
backup_report.txt
```

A duplicate copy is created.

---

### Example 2: Copy a Directory

```bash
cp -r project project_backup
```

Before:

```text
project/
```

After:

```text
project/
project_backup/
```

The entire directory and its contents are copied.

---

### Example 3: Interactive Copy

```bash
cp -i config.conf /etc/myapp/
```

Output:

```text
cp: overwrite '/etc/myapp/config.conf'? 
```

The system asks for confirmation before replacing the existing file.

---

### Example 4: Verbose Copy

```bash
cp -v app.log backup/
```

Output:

```text
'app.log' -> 'backup/app.log'
```

Useful for scripts and troubleshooting.

---

## Common Use Cases

### 1. Create a Backup Before Editing

```bash
cp nginx.conf nginx.conf.bak
```

Always create a backup before modifying configuration files.

---

### 2. Backup an Entire Application Directory

```bash
cp -r /etc/myapp /backup/myapp_backup
```

Useful before upgrades or maintenance.

---

### 3. Create a New File from a Template

```bash
cp config.template config.conf
```

Common during deployments and project setup.

---

### 4. Copy Build Output During Deployment

```bash
cp -r build/* /var/www/html/
```

Used to deploy web applications.

---

### 5. Preserve File Attributes

```bash
cp -p report.txt backup/
```

Preserves:

* Permissions
* Ownership
* Timestamps

---

### 6. Prevent Accidental Overwrites

```bash
cp -n data.csv backup/
```

Existing files remain untouched.

---

### 7. Copy Only Updated Files

```bash
cp -u report.txt backup/
```

Copies only if the source file is newer.

---

### 8. Archive Log Files

```bash
cp *.log /archive/logs/
```

Store logs for auditing and troubleshooting.

---

### 9. Copy Multiple Files

```bash
cp file1.txt file2.txt file3.txt /backup/
```

Copy several files in one command.

---

### 10. Full Backup Using Archive Mode

```bash
cp -a project/ project_backup/
```

Preserves:

* Permissions
* Symbolic links
* Ownership
* Timestamps
* Directory structure

---

## Important Options Explained

### Recursive Copy (-r)

Required for directories.

```bash
cp -r source_dir destination_dir
```

Without `-r`, directories cannot be copied.

---

### Archive Mode (-a)

Best option for backups.

```bash
cp -a source destination
```

Equivalent to preserving almost all file metadata.

---

### Interactive Mode (-i)

```bash
cp -i file.txt backup/
```

Prevents accidental overwrites.

Recommended for production environments.

---

## Common Interview Questions

### Q1. What is the difference between `cp` and `mv`?

| cp                | mv                |
| ----------------- | ----------------- |
| Creates a copy    | Moves the file    |
| Source remains    | Source is removed |
| Duplicate created | No duplicate      |

---

### Q2. Why is `-r` required?

Directories contain multiple files and subdirectories.

The `-r` flag tells Linux to copy everything recursively.

---

### Q3. What does `cp -a` do?

Archive mode:

* Preserves permissions
* Preserves ownership
* Preserves timestamps
* Preserves symbolic links

Used for backups and migrations.

---

### Q4. How do you avoid overwriting files?

```bash
cp -i file.txt destination/
```

or

```bash
cp -n file.txt destination/
```

---

## Related Commands

* mv
* rsync
* tar
* scp
* find

---

## Notes

* Always use `cp -i` when working with important files.
* Use `cp -a` for backups.
* Use `rsync` instead of `cp` for large synchronization tasks.
* Verify copied files using `ls -l` after completion.

---

## References

```bash
man cp
info cp
```

---

## Quick Cheat Sheet

```bash
cp file.txt backup.txt
cp -r project project_backup
cp -i file.txt destination/
cp -v file.txt destination/
cp -n file.txt destination/
cp -u file.txt destination/
cp -a source destination
cp *.log /archive/
```
