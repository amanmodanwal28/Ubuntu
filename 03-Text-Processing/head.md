# head — View Beginning of a File

## Purpose

The `head` command displays the first lines of a file.

By default, it shows the **first 10 lines**.

It is commonly used for:

* Checking file contents quickly
* Viewing log file headers
* Inspecting CSV files
* Reading configuration files
* Verifying command output

`head` is the opposite of `tail`.

---

## Syntax

```bash
head [options] file_name
```

Example:

```bash
head app.log
```

---

## Common Commands

| Command                | Description                   |
| ---------------------- | ----------------------------- |
| `head file.txt`        | Show first 10 lines           |
| `head -n 20 file.txt`  | Show first 20 lines           |
| `head -n 50 file.txt`  | Show first 50 lines           |
| `head -n -10 file.txt` | Show all except last 10 lines |
| `head -c 100 file.txt` | Show first 100 bytes          |
| `head -q file1 file2`  | Suppress file headers         |
| `head -v file1 file2`  | Always show file headers      |

---

## Examples

### Example 1: Display First 10 Lines

```bash
head notes.txt
```

Output:

```text
Line 1
Line 2
Line 3
...
Line 10
```

---

### Example 2: Display First 20 Lines

```bash
head -n 20 app.log
```

Useful when inspecting log files.

---

### Example 3: Display First 100 Bytes

```bash
head -c 100 file.txt
```

Output:

```text
First 100 bytes of file
```

Useful for binary files and data inspection.

---

### Example 4: Multiple Files

```bash
head file1.txt file2.txt
```

Output:

```text
==> file1.txt <==
...

==> file2.txt <==
...
```

---

### Example 5: Suppress Headers

```bash
head -q file1.txt file2.txt
```

Displays contents without filename headers.

---

## Common Use Cases

### 1. Check Beginning of Log File

```bash
head app.log
```

Shows initial startup messages.

---

### 2. Verify CSV Header

```bash
head employees.csv
```

Output:

```text
ID,Name,Department,Salary
```

Useful before processing data.

---

### 3. Inspect Configuration Files

```bash
head /etc/passwd
```

View first few entries.

---

### 4. Preview Large Files

```bash
head largefile.txt
```

Avoid opening the entire file.

---

### 5. Check Script Header

```bash
head deploy.sh
```

Output:

```text
#!/bin/bash
```

Verify interpreter quickly.

---

### 6. View First 50 Lines of Source Code

```bash
head -n 50 main.py
```

Useful when reviewing code.

---

### 7. Inspect Downloaded Data

```bash
head data.csv
```

Verify correct format before importing.

---

### 8. View Command Output

```bash
ps aux | head
```

Shows only first few processes.

---

## Practical Examples

### Show First 5 Lines

```bash
head -n 5 file.txt
```

---

### View Top Processes

```bash
ps aux | head
```

---

### View Installed Packages

```bash
dpkg -l | head
```

Ubuntu systems.

---

### Check System Users

```bash
head /etc/passwd
```

---

### Inspect Log Start

```bash
head /var/log/syslog
```

---

### Read First 20 Lines of Python Script

```bash
head -n 20 script.py
```

---

## head vs tail

| Command | Purpose           |
| ------- | ----------------- |
| `head`  | Beginning of file |
| `tail`  | End of file       |

Example:

```bash
head app.log
tail app.log
```

---

## head vs cat

| Feature               | head      | cat  |
| --------------------- | --------- | ---- |
| Show first lines only | Yes       |      |
| Show entire file      | No        | Yes  |
| Large file preview    | Excellent | Poor |

---

## Common Interview Questions

### Q1. What does head do?

Displays the first lines of a file.

---

### Q2. How many lines are shown by default?

```text
10 lines
```

---

### Q3. How do you display first 50 lines?

```bash
head -n 50 file.txt
```

---

### Q4. How do you display first 100 bytes?

```bash
head -c 100 file.txt
```

---

### Q5. What is the opposite of head?

```text
tail
```

---

## Real-World Examples

### Check CSV Header

```bash
head customers.csv
```

---

### Check Python Script

```bash
head app.py
```

---

### View Docker Logs Export

```bash
head container.log
```

---

### Inspect Nginx Access Logs

```bash
head /var/log/nginx/access.log
```

---

### Preview API Response File

```bash
head response.json
```

---

## Related Commands

* tail
* cat
* less
* more
* tac
* grep

---

## Notes

* `head` is one of the fastest ways to inspect files.
* Commonly used before processing large datasets.
* Often combined with pipes (`|`).
* Useful for log analysis and debugging.
* Opposite of `tail`.

---

## References

```bash
man head
info head
```

---

## Quick Cheat Sheet

```bash
head file.txt
head -n 20 file.txt
head -n 50 file.txt
head -c 100 file.txt

ps aux | head
dpkg -l | head
head /etc/passwd
head app.log
head customers.csv
```
