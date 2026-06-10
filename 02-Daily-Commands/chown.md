# chown — Change File and Directory Ownership

## Purpose

The `chown` command stands for **Change Owner**.

It is used to change the ownership of files and directories in Linux.

Every file in Linux has:

* An Owner (User)
* A Group

The owner determines who has primary control over the file, while the group defines which users can access it based on group permissions.

`chown` is commonly used by system administrators, DevOps engineers, and developers when deploying applications, managing services, or fixing permission issues.

---

## Syntax

```bash
chown [options] user[:group] file
```

---

## Ownership Basics

Check ownership using:

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 aman developers 2048 Jun 10 app.conf
```

Breakdown:

```text
Owner : aman
Group : developers
```

---

## Common Commands

| Command                         | Description                      |
| ------------------------------- | -------------------------------- |
| `chown user file`               | Change owner only                |
| `chown user:group file`         | Change owner and group           |
| `chown :group file`             | Change group only                |
| `chown -R user:group dir/`      | Change ownership recursively     |
| `chown -v user file`            | Show detailed output             |
| `chown --reference=file1 file2` | Copy ownership from another file |

---

## Examples

### Example 1: Change File Owner

```bash
sudo chown aman report.txt
```

Before:

```text
-rw-r--r-- root root report.txt
```

After:

```text
-rw-r--r-- aman root report.txt
```

The file owner changes from `root` to `aman`.

---

### Example 2: Change Owner and Group

```bash
sudo chown aman:developers project.conf
```

Before:

```text
-rw-r--r-- root root project.conf
```

After:

```text
-rw-r--r-- aman developers project.conf
```

Both owner and group are updated.

---

### Example 3: Change Group Only

```bash
sudo chown :developers app.log
```

Result:

```text
Owner : unchanged
Group : developers
```

Only the group ownership changes.

---

### Example 4: Recursive Ownership Change

```bash
sudo chown -R appuser:appuser /opt/app
```

Applies ownership changes to:

* Directory
* Subdirectories
* Files

---

### Example 5: Verbose Mode

```bash
sudo chown -v aman report.txt
```

Output:

```text
changed ownership of 'report.txt' from root to aman
```

Useful for scripts and troubleshooting.

---

## Common Use Cases

### 1. Web Server Files

```bash
sudo chown -R www-data:www-data /var/www/html
```

Used with:

* Apache
* Nginx
* PHP applications

Ensures the web server can access website files.

---

### 2. Application Deployment

```bash
sudo chown -R appuser:appuser /opt/myapp
```

After deployment, application files should belong to the service account.

---

### 3. PostgreSQL Database Files

```bash
sudo chown postgres:postgres /var/lib/postgresql
```

Database files must belong to the PostgreSQL service user.

---

### 4. Fix Docker Container File Ownership

```bash
sudo chown -R aman:aman project/
```

Useful when Docker creates files owned by root.

---

### 5. Shared Team Directory

```bash
sudo chown -R aman:developers /shared/project
```

Allows team members in the developers group to collaborate.

---

### 6. Transfer Project Ownership

```bash
sudo chown -R newuser:newuser project/
```

Useful when moving projects between users.

---

### 7. Home Directory Recovery

```bash
sudo chown -R aman:aman /home/aman
```

Restores ownership after accidental permission changes.

---

### 8. Web Upload Directory

```bash
sudo chown -R www-data:www-data uploads/
```

Allows web applications to store uploaded files.

---

## Understanding Owner and Group

Example:

```text
-rwxr-xr-- 1 aman developers app.sh
```

| Field  | Value         |
| ------ | ------------- |
| Owner  | aman          |
| Group  | developers    |
| Others | Everyone else |

Permissions are applied separately to:

1. Owner
2. Group
3. Others

---

## Recursive Ownership Change

### Without -R

```bash
sudo chown aman project/
```

Only the directory changes.

Files inside remain unchanged.

---

### With -R

```bash
sudo chown -R aman project/
```

Everything inside changes ownership.

Example:

```text
project/
├── app.py
├── config.conf
└── logs/
```

All files and folders receive the new owner.

---

## Difference Between chown and chmod

| Command | Purpose            |
| ------- | ------------------ |
| `chown` | Change owner/group |
| `chmod` | Change permissions |

Example:

```bash
sudo chown aman file.txt
chmod 644 file.txt
```

First changes ownership.

Second changes permissions.

---

## Common Interview Questions

### Q1. What does chown stand for?

Change Owner.

---

### Q2. What is the difference between chown and chmod?

`chown` changes ownership.

`chmod` changes permissions.

---

### Q3. How do you change both owner and group?

```bash
sudo chown user:group file
```

Example:

```bash
sudo chown aman:developers app.py
```

---

### Q4. What does the -R option do?

Recursive ownership change.

Applies to all files and directories below the specified path.

---

### Q5. Why do web applications often use www-data ownership?

Because Apache and Nginx services typically run under the `www-data` user.

They need ownership or appropriate permissions to access files.

---

## Security Notes

### Avoid Unnecessary Ownership Changes

Bad Example:

```bash
sudo chown -R nobody:nobody /
```

This can break the operating system.

---

### Verify Before Changing

Check ownership first:

```bash
ls -l
```

Then apply changes only where necessary.

---

### Use Least Privilege Principle

Grant ownership only to users who require access.

Avoid giving application files ownership by root unless required.

---

## Related Commands

* chmod
* ls
* stat
* groups
* id
* umask

---

## Notes

* Root privileges are usually required.
* Ownership controls access and security.
* Commonly used after deployments and migrations.
* Frequently used alongside `chmod`.

Verify ownership:

```bash
ls -l
```

---

## References

```bash
man chown
info chown
```

---

## Quick Cheat Sheet

```bash
sudo chown user file
sudo chown user:group file
sudo chown :group file
sudo chown -R user:group directory/
sudo chown -v user file
ls -l
id
groups
```
