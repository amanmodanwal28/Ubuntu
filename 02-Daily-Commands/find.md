# find — Search Files and Directories

## Purpose

The `find` command is one of the most powerful Linux utilities used to search for files and directories within a directory tree.

It can search based on:

* File name
* File type
* File size
* Owner
* Permissions
* Modification time
* Empty files/directories

In addition to searching, `find` can perform actions on matched files such as deleting, moving, copying, or changing permissions.

---

## Syntax

```bash
find [path] [options] [expression]
```

---

## Common Search Options

| Command                                         | Description                   |
| ----------------------------------------------- | ----------------------------- |
| `find /path -name "file.txt"`                   | Search by exact filename      |
| `find /path -name "*.log"`                      | Search using wildcard pattern |
| `find /path -iname "*.Log"`                     | Case-insensitive search       |
| `find /path -type f`                            | Search only files             |
| `find /path -type d`                            | Search only directories       |
| `find /path -type l`                            | Search only symbolic links    |
| `find /path -size +10M`                         | Files larger than 10 MB       |
| `find /path -size -1M`                          | Files smaller than 1 MB       |
| `find /path -mtime -7`                          | Modified within last 7 days   |
| `find /path -mtime +30`                         | Older than 30 days            |
| `find /path -perm 777`                          | Specific permission search    |
| `find /path -user username`                     | Files owned by a user         |
| `find /path -empty`                             | Empty files/directories       |
| `find /path -maxdepth 2`                        | Search only 2 levels deep     |
| `find /path -name "*.log" -delete`              | Search and delete             |
| `find /path -name "*.py" -exec chmod 644 {} \;` | Execute command on results    |

---

## Examples

### Example 1: Search by File Name

```bash
find /home/aman -name "report.txt"
```

Output:

```text
/home/aman/Documents/report.txt
```

Finds the exact file name.

---

### Example 2: Search All Log Files

```bash
find /var/log -name "*.log"
```

Output:

```text
/var/log/syslog.log
/var/log/nginx/access.log
/var/log/nginx/error.log
```

Lists all log files.

---

### Example 3: Search Directories Only

```bash
find . -type d
```

Output:

```text
.
./Documents
./Downloads
./Projects
```

Displays only directories.

---

### Example 4: Search Files Larger Than 100 MB

```bash
find / -size +100M
```

Output:

```text
/usr/local/bigfile.iso
/home/aman/video.mp4
```

Useful for disk cleanup.

---

### Example 5: Search Recently Modified Files

```bash
find . -mtime -1
```

Shows files modified within the last 24 hours.

---

## Common Use Cases

### 1. Find a Configuration File

```bash
find / -name "config.ini"
```

Locate configuration files anywhere on the system.

---

### 2. Delete Old Log Files

```bash
find /var/log -name "*.log" -mtime +30 -delete
```

Delete logs older than 30 days.

---

### 3. Audit Dangerous Permissions

```bash
find / -perm 777
```

Find files with full permissions.

Useful for security audits.

---

### 4. Find Empty Directories

```bash
find . -type d -empty
```

Locate unused directories.

---

### 5. Find Large Files

```bash
find / -size +100M
```

Identify files consuming disk space.

---

### 6. Find Recently Modified Files

```bash
find . -mtime -1
```

Locate files changed during the last day.

---

### 7. Exclude node_modules

```bash
find . -not -path "*/node_modules/*" -name "*.js"
```

Search JavaScript files while skipping dependencies.

---

### 8. Security Audit for SUID Files

```bash
find / -perm /4000
```

Find files with the SUID bit set.

Examples:

```text
/usr/bin/passwd
/usr/bin/sudo
```

Useful for Linux security reviews.

---

### 9. Find Files Owned by a User

```bash
find /home -user aman
```

Search files belonging to a specific user.

---

### 10. Find Empty Files

```bash
find . -type f -empty
```

Locate zero-byte files.

---

## File Type Options

| Type      | Meaning          |
| --------- | ---------------- |
| `-type f` | Regular file     |
| `-type d` | Directory        |
| `-type l` | Symbolic link    |
| `-type b` | Block device     |
| `-type c` | Character device |
| `-type p` | Named pipe       |
| `-type s` | Socket           |

Example:

```bash
find /dev -type b
```

Lists block devices.

---

## Size Search Examples

### Larger Than 10 MB

```bash
find . -size +10M
```

### Smaller Than 1 MB

```bash
find . -size -1M
```

### Exactly 100 MB

```bash
find . -size 100M
```

---

## Time-Based Search Examples

### Modified Today

```bash
find . -mtime -1
```

### Older Than 30 Days

```bash
find . -mtime +30
```

### Accessed Within Last 7 Days

```bash
find . -atime -7
```

### Changed Within Last 24 Hours

```bash
find . -ctime -1
```

---

## Executing Commands on Results

### Change Permissions

```bash
find . -name "*.sh" -exec chmod +x {} \;
```

Make all shell scripts executable.

---

### Delete Matching Files

```bash
find . -name "*.tmp" -delete
```

Delete temporary files.

---

### Move Files

```bash
find . -name "*.log" -exec mv {} archive/ \;
```

Move log files to an archive directory.

---

## Difference Between find and locate

| find                     | locate            |
| ------------------------ | ----------------- |
| Searches filesystem live | Uses database     |
| Slower                   | Faster            |
| Very flexible            | Limited filtering |
| Always accurate          | May be outdated   |

Example:

```bash
find / -name "test.txt"
```

```bash
locate test.txt
```

---

## Common Interview Questions

### Q1. What is the difference between find and locate?

`find` performs a real-time filesystem search.

`locate` searches a prebuilt database.

---

### Q2. How do you find files larger than 1 GB?

```bash
find / -size +1G
```

---

### Q3. How do you search case-insensitively?

```bash
find . -iname "*.log"
```

---

### Q4. How do you delete files found by find?

```bash
find . -name "*.tmp" -delete
```

or

```bash
find . -name "*.tmp" -exec rm {} \;
```

---

### Q5. How do you find all directories?

```bash
find . -type d
```

---

## Related Commands

* locate
* grep
* ls
* du
* chmod
* rm

---

## Notes

* `find` is one of the most important Linux commands.
* Always test searches before using `-delete`.
* Use `-exec` carefully because it executes commands automatically.
* Commonly used by system administrators, DevOps engineers, developers, and security professionals.

---

## References

```bash
man find
info find
```

---

## Quick Cheat Sheet

```bash
find . -name "*.txt"
find . -iname "*.log"
find . -type f
find . -type d
find . -size +100M
find . -mtime -7
find . -empty
find . -user aman
find . -perm 777
find . -name "*.tmp" -delete
find . -name "*.sh" -exec chmod +x {} \;
```
