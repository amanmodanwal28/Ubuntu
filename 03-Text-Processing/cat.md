# cat — Concatenate and Display File Contents

## Purpose

The `cat` command stands for **Concatenate**.

It is used to:

* Display file contents
* Combine multiple files
* Create small text files
* View configuration files
* Read virtual system files

`cat` is one of the most commonly used Linux commands for quickly viewing file contents.

---

## Syntax

```bash
cat [options] file_name
```

---

## Common Commands

| Command                        | Description                   |
| ------------------------------ | ----------------------------- |
| `cat file.txt`                 | Display file content          |
| `cat -n file.txt`              | Display with line numbers     |
| `cat -A file.txt`              | Show hidden characters        |
| `cat -s file.txt`              | Compress multiple blank lines |
| `cat file1 file2`              | Display multiple files        |
| `cat file1 file2 > output.txt` | Merge files into one          |
| `cat > file.txt`               | Create a new file             |
| `cat >> file.txt`              | Append content to a file      |

---

## Examples

### Example 1: Display a File

Create a file:

```bash
echo "Hello Linux" > notes.txt
```

View content:

```bash
cat notes.txt
```

Output:

```text
Hello Linux
```

---

### Example 2: Display Line Numbers

```bash
cat -n notes.txt
```

Output:

```text
1  Hello Linux
```

Useful when debugging scripts and configuration files.

---

### Example 3: Display Multiple Files

```bash
cat file1.txt file2.txt
```

Output:

```text
Content of file1
Content of file2
```

Displays both files sequentially.

---

### Example 4: Merge Two Files

```bash
cat part1.txt part2.txt > full.txt
```

Contents:

**part1.txt**

```text
Linux
```

**part2.txt**

```text
Ubuntu
```

Result:

```bash
cat full.txt
```

Output:

```text
Linux
Ubuntu
```

---

### Example 5: Show Hidden Characters

```bash
cat -A script.sh
```

Output:

```text
echo Hello$
```

Symbols shown:

| Symbol | Meaning       |
| ------ | ------------- |
| `$`    | End of line   |
| `^I`   | Tab character |

Useful for debugging line-ending issues.

---

## Create Files Using cat

### Create New File

```bash
cat > notes.txt
```

Type:

```text
Linux Commands
Ubuntu Basics
```

Press:

```text
Ctrl + D
```

Save and exit.

Verify:

```bash
cat notes.txt
```

Output:

```text
Linux Commands
Ubuntu Basics
```

---

### Append Content

```bash
cat >> notes.txt
```

Add:

```text
Shell Scripting
```

Press:

```text
Ctrl + D
```

Result:

```text
Linux Commands
Ubuntu Basics
Shell Scripting
```

---

## Common Use Cases

### 1. View Configuration Files

```bash
cat /etc/hostname
```

Output:

```text
ubuntu-server
```

Useful for system administration.

---

### 2. View Small Log Files

```bash
cat application.log
```

Displays log content instantly.

---

### 3. Read System Information

CPU Information:

```bash
cat /proc/cpuinfo
```

Memory Information:

```bash
cat /proc/meminfo
```

Kernel Version:

```bash
cat /proc/version
```

---

### 4. Merge Files

```bash
cat chapter1.txt chapter2.txt > book.txt
```

Creates a combined file.

---

### 5. Debug Shell Scripts

```bash
cat -n deploy.sh
```

Shows line numbers.

---

### 6. Detect Windows Line Endings

```bash
cat -A script.sh
```

May show:

```text
echo Hello^M$
```

`^M` indicates Windows CRLF line endings.

---

### 7. Display Environment Files

```bash
cat .env
```

Example:

```text
PORT=8080
DEBUG=true
```

---

### 8. View SSH Public Key

```bash
cat ~/.ssh/id_rsa.pub
```

Used when copying SSH keys to servers.

---

## Important Notes

### cat Loads Everything at Once

Good for:

```text
Small files
Config files
Scripts
```

Not ideal for:

```text
Large logs
Huge datasets
Very large text files
```

For large files use:

```bash
less file.log
```

or

```bash
more file.log
```

---

## cat vs less vs more

| Command | Best For          |
| ------- | ----------------- |
| cat     | Small files       |
| less    | Large files       |
| more    | Simple paging     |
| head    | Beginning of file |
| tail    | End of file       |

Example:

```bash
cat config.conf
less server.log
tail app.log
```

---

## Common Interview Questions

### Q1. What does cat stand for?

Concatenate.

---

### Q2. How do you display a file?

```bash
cat file.txt
```

---

### Q3. How do you merge files?

```bash
cat file1 file2 > merged.txt
```

---

### Q4. How do you show line numbers?

```bash
cat -n file.txt
```

---

### Q5. How do you create a file using cat?

```bash
cat > file.txt
```

Type content and press:

```text
Ctrl + D
```

---

## Practical Examples

### View Hostname

```bash
cat /etc/hostname
```

---

### View CPU Information

```bash
cat /proc/cpuinfo
```

---

### View Memory Information

```bash
cat /proc/meminfo
```

---

### Merge Logs

```bash
cat app1.log app2.log > combined.log
```

---

### Show Script with Line Numbers

```bash
cat -n script.sh
```

---

## Related Commands

* less
* more
* head
* tail
* tac
* grep
* echo

---

## Notes

* Best for viewing small files.
* Frequently used with configuration files.
* Useful for reading Linux virtual files in `/proc`.
* Can create and merge files.
* For large files, prefer `less`.

---

## References

```bash
man cat
info cat
```

---

## Quick Cheat Sheet

```bash
cat file.txt
cat -n file.txt
cat -A file.txt
cat -s file.txt
cat file1 file2
cat file1 file2 > merged.txt
cat > newfile.txt
cat >> existing.txt
cat /proc/cpuinfo
cat /proc/meminfo
cat /etc/hostname
```
