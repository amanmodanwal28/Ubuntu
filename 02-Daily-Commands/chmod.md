# chmod — Change File and Directory Permissions

## Purpose

The `chmod` command stands for **Change Mode**.

It is used to change the permissions of files and directories in Linux.

Permissions control who can:

* Read a file
* Write to a file
* Execute a file

Proper permission management is critical for Linux security, system administration, and application deployment.

---

## Syntax

```bash
chmod [options] permissions file
```

---

## Linux Permission Basics

Linux permissions are divided into three categories:

| Category     | Symbol | Meaning                      |
| ------------ | ------ | ---------------------------- |
| User (Owner) | u      | File owner                   |
| Group        | g      | Users belonging to the group |
| Others       | o      | Everyone else                |
| All          | a      | User + Group + Others        |

---

## Permission Values

```text
4 = Read (r)
2 = Write (w)
1 = Execute (x)
```

### Permission Calculation

| Value | Permission |
| ----- | ---------- |
| 0     | ---        |
| 1     | --x        |
| 2     | -w-        |
| 3     | -wx        |
| 4     | r--        |
| 5     | r-x        |
| 6     | rw-        |
| 7     | rwx        |

---

## Permission Structure

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
Owner   = rwx = 7
Group   = r-x = 5
Others  = r-- = 4
```

Numeric form:

```text
754
```

---

## Common Permission Values

| Value | Permissions | Common Use Case                   |
| ----- | ----------- | --------------------------------- |
| 755   | rwxr-xr-x   | Directories, executable scripts   |
| 644   | rw-r--r--   | Regular files                     |
| 600   | rw-------   | SSH private keys                  |
| 700   | rwx------   | Private scripts                   |
| 400   | r--------   | Sensitive configuration files     |
| 777   | rwxrwxrwx   | Full access (avoid in production) |

---

## Common Commands

| Command                  | Description                       |
| ------------------------ | --------------------------------- |
| `chmod 755 file`         | Set permissions numerically       |
| `chmod +x file`          | Add execute permission            |
| `chmod -x file`          | Remove execute permission         |
| `chmod u+x file`         | Add execute for owner             |
| `chmod g+w file`         | Add write permission for group    |
| `chmod o-r file`         | Remove read permission for others |
| `chmod a+r file`         | Add read permission for everyone  |
| `chmod -R 755 directory` | Apply permissions recursively     |

---

## Examples

### Example 1: Make a Script Executable

```bash
chmod +x deploy.sh
```

Before:

```text
-rw-r--r--
```

After:

```text
-rwxr-xr-x
```

Now the script can be executed.

Run:

```bash
./deploy.sh
```

---

### Example 2: Set Standard File Permissions

```bash
chmod 644 index.html
```

Result:

```text
-rw-r--r--
```

Suitable for web pages and regular documents.

---

### Example 3: Secure an SSH Private Key

```bash
chmod 600 ~/.ssh/id_rsa
```

Result:

```text
-rw-------
```

Only the owner can read and write.

SSH often refuses keys with weaker permissions.

---

### Example 4: Make a Directory Accessible

```bash
chmod 755 project/
```

Result:

```text
drwxr-xr-x
```

Owner has full control.

Others can read and enter the directory.

---

### Example 5: Apply Permissions Recursively

```bash
chmod -R 755 /opt/myapp
```

Applies permissions to:

* Directory
* Subdirectories
* Files

---

## Symbolic Mode Examples

### Add Execute Permission

```bash
chmod +x script.sh
```

---

### Remove Execute Permission

```bash
chmod -x script.sh
```

---

### Add Write Permission to Group

```bash
chmod g+w report.txt
```

---

### Remove Read Permission from Others

```bash
chmod o-r confidential.txt
```

---

### Give Everyone Read Access

```bash
chmod a+r document.pdf
```

---

## Common Use Cases

### 1. Make Shell Scripts Executable

```bash
chmod +x deploy.sh
```

Most common use of chmod.

---

### 2. Secure SSH Keys

```bash
chmod 600 ~/.ssh/id_rsa
```

Required for SSH authentication.

---

### 3. Set Web Server File Permissions

```bash
chmod 644 index.html
```

Allows web server access while protecting modifications.

---

### 4. Protect Sensitive Configuration Files

```bash
chmod 400 production.conf
```

Read-only access for owner.

---

### 5. Reset Application Permissions

```bash
chmod -R 755 /opt/myapp
```

Useful after deployments.

---

### 6. Secure Backup Files

```bash
chmod 600 backup.tar.gz
```

Prevent unauthorized access.

---

### 7. Create Private Directories

```bash
chmod 700 private_data/
```

Only the owner can access.

---

## Understanding 755 vs 644

### 755

```text
Owner  : rwx
Group  : r-x
Others : r-x
```

Use for:

* Directories
* Executable scripts

---

### 644

```text
Owner  : rw-
Group  : r--
Others : r--
```

Use for:

* Text files
* Configuration files
* HTML files

---

## ⚠️ Security Warning

Avoid:

```bash
chmod 777 file
```

Result:

```text
rwxrwxrwx
```

Everyone gets:

* Read access
* Write access
* Execute access

This creates major security risks.

Only use temporarily for testing.

---

## Common Interview Questions

### Q1. What does chmod stand for?

Change Mode.

---

### Q2. What does chmod 755 mean?

```text
Owner  : rwx
Group  : r-x
Others : r-x
```

Numeric calculation:

```text
7 = 4 + 2 + 1 = rwx
5 = 4 + 1     = r-x
5 = 4 + 1     = r-x
```

---

### Q3. What is the difference between 755 and 777?

755:

```text
rwxr-xr-x
```

777:

```text
rwxrwxrwx
```

777 allows everyone full access and is generally unsafe.

---

### Q4. Why does SSH require chmod 600?

SSH private keys must be protected from other users.

If permissions are too open, SSH rejects the key.

---

### Q5. What does chmod -R do?

Applies permissions recursively to all files and subdirectories.

---

## Related Commands

* chown
* umask
* ls
* find
* stat

---

## Notes

* Use 644 for regular files.
* Use 755 for directories and executable scripts.
* Use 600 for SSH private keys.
* Avoid 777 whenever possible.
* Always verify permissions using:

```bash
ls -l
```

---

## References

```bash
man chmod
info chmod
```

---

## Quick Cheat Sheet

```bash
chmod 755 script.sh
chmod 644 file.txt
chmod 600 ~/.ssh/id_rsa
chmod +x script.sh
chmod -x script.sh
chmod g+w file.txt
chmod o-r file.txt
chmod a+r file.txt
chmod -R 755 project/
ls -l
```
