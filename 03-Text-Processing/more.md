# more — View File Contents Page by Page

## Purpose

The `more` command is a **pager** used to display file contents one screen at a time.

It was one of the earliest Linux/Unix tools for viewing large text files before `less` became popular.

`more` allows you to:

* Read files page by page
* View long command outputs
* Avoid terminal flooding from large files

However, compared to `less`, it has fewer navigation features.

---

## Syntax

```bash
more [options] file_name
```

Example:

```bash
more logfile.txt
```

---

## Why Use more?

If a file contains hundreds or thousands of lines:

```bash
cat logfile.txt
```

The entire file is dumped to the terminal.

Instead:

```bash
more logfile.txt
```

Shows one screen at a time.

---

## Common Commands

| Command             | Description                    |
| ------------------- | ------------------------------ |
| `more file.txt`     | Open file page by page         |
| `command \| more`   | Page command output            |
| `more +10 file.txt` | Start from line 10             |
| `more -d file.txt`  | Display helpful prompts        |
| `more -c file.txt`  | Clear screen before displaying |

---

## Navigation Keys

| Key        | Action         |
| ---------- | -------------- |
| `Space`    | Next page      |
| `Enter`    | Next line      |
| `q`        | Quit           |
| `/pattern` | Search forward |
| `n`        | Next match     |

---

## Examples

### Example 1: Open a File

```bash
more notes.txt
```

Output:

```text
Line 1
Line 2
Line 3
--More--
```

Press:

```text
Space
```

to continue.

---

### Example 2: Open Large Log File

```bash
more application.log
```

Displays:

```text
One page at a time
```

instead of flooding the terminal.

---

### Example 3: Start from Specific Line

```bash
more +100 logfile.txt
```

Starts reading from line 100.

Useful when checking large logs.

---

### Example 4: Read Command Output

```bash
ps aux | more
```

Displays running processes page by page.

---

### Example 5: View Kernel Messages

```bash
dmesg | more
```

Useful for hardware troubleshooting.

---

## Common Use Cases

### 1. Read Large Files

```bash
more server.log
```

---

### 2. View Configuration Files

```bash
more /etc/passwd
```

---

### 3. Page Long Command Output

```bash
find / -name "*.conf" | more
```

---

### 4. View Running Processes

```bash
ps aux | more
```

---

### 5. View Package Lists

```bash
dpkg -l | more
```

Ubuntu systems.

---

### 6. Read System Logs

```bash
more /var/log/syslog
```

---

### 7. Read Network Information

```bash
ip addr | more
```

---

### 8. View Environment Variables

```bash
env | more
```

---

## Search Inside more

Open file:

```bash
more file.txt
```

Search:

```text
/error
```

Linux jumps to the next occurrence.

---

## more vs cat

| Feature                  | more  | cat |
| ------------------------ | ----- | --- |
| Page-by-page viewing     | Yes   | No  |
| Search support           | Basic | No  |
| Suitable for large files | Yes   | No  |
| Interactive              | Yes   | No  |

Example:

```bash
cat large.log
```

vs

```bash
more large.log
```

---

## more vs less

| Feature                  | more    | less      |
| ------------------------ | ------- | --------- |
| Forward scrolling        | Yes     | Yes       |
| Backward scrolling       | Limited | Yes       |
| Search                   | Basic   | Advanced  |
| Large file support       | Good    | Excellent |
| Most commonly used today | No      | Yes       |

Most Linux administrators prefer:

```bash
less file.txt
```

instead of:

```bash
more file.txt
```

because it offers more features.

---

## Common Interview Questions

### Q1. What is more?

A pager that displays file contents one screen at a time.

---

### Q2. Why use more instead of cat?

Because it prevents large files from flooding the terminal.

---

### Q3. How do you quit more?

Press:

```text
q
```

---

### Q4. How do you move to the next page?

Press:

```text
Space
```

---

### Q5. Which is better: more or less?

Generally:

```text
less
```

because it supports:

* Forward navigation
* Backward navigation
* Better searching
* More features

---

## Practical Examples

### Read System Log

```bash
more /var/log/syslog
```

---

### Read passwd File

```bash
more /etc/passwd
```

---

### View Running Processes

```bash
ps aux | more
```

---

### View Network Configuration

```bash
ip addr | more
```

---

### View Search Results

```bash
find / -name "*.log" | more
```

---

### Read Large Text File

```bash
more book.txt
```

---

## Related Commands

* less
* cat
* head
* tail
* grep
* dmesg
* journalctl

---

## Notes

* `more` was one of the first Unix pagers.
* Suitable for medium-sized files.
* `less` is generally preferred today.
* Useful for reading logs and long command outputs.
* Works well with pipes (`|`).

---

## References

```bash
man more
info more
```

---

## Quick Cheat Sheet

```bash
more file.txt
more +100 file.txt
more -d file.txt
more -c file.txt

ps aux | more
dmesg | more
find / -name "*.conf" | more

Space
Enter
/search
n
q
```
