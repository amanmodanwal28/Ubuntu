# tac — Reverse cat

## Purpose

`tac` is the reverse version of the `cat` command.

While `cat` displays a file from the first line to the last line, `tac` displays the file from the last line to the first line.

The name **tac** is simply **cat spelled backward**.

---

## Syntax

```bash
tac [options] file_name
```

Example:

```bash
tac notes.txt
```

---

## cat vs tac

### File Content

```text
Line 1
Line 2
Line 3
Line 4
```

### Using cat

```bash
cat notes.txt
```

Output:

```text
Line 1
Line 2
Line 3
Line 4
```

### Using tac

```bash
tac notes.txt
```

Output:

```text
Line 4
Line 3
Line 2
Line 1
```

---

## Common Commands

| Command                    | Description                         |
| -------------------------- | ----------------------------------- |
| `tac file.txt`             | Display file in reverse order       |
| `tac log.txt`              | Show newest entries first           |
| `tac file \| grep pattern` | Search from bottom of file          |
| `tac file \| less`         | Reverse view with scrolling         |
| `tac file \| head -10`     | Show last 10 lines in reverse order |

---

## Examples

### Example 1: Reverse a File

File:

```text
Linux
Ubuntu
Debian
Fedora
```

Command:

```bash
tac distro.txt
```

Output:

```text
Fedora
Debian
Ubuntu
Linux
```

---

### Example 2: Reverse Log File

```bash
tac application.log
```

Shows latest log entries first.

---

### Example 3: View Reverse Output with less

```bash
tac application.log | less
```

Useful for large files.

---

### Example 4: Show Recent Errors First

```bash
tac app.log | grep ERROR
```

Displays matching errors starting from the newest entries.

---

### Example 5: Show Last 20 Lines in Reverse

```bash
tac app.log | head -20
```

Useful when recent log entries are most important.

---

## Common Use Cases

### 1. Read Log Files from Bottom

```bash
tac app.log
```

Most logs store newest entries at the bottom.

---

### 2. Investigate Recent Errors

```bash
tac app.log | grep ERROR
```

Find latest errors first.

---

### 3. Analyze System Logs

```bash
tac /var/log/syslog
```

Review newest events before older ones.

---

### 4. Search Recent Login Activity

```bash
tac /var/log/auth.log
```

Shows latest login attempts first.

---

### 5. Combine with head

```bash
tac app.log | head -50
```

Display the newest 50 log entries.

---

### 6. Reverse Command Output

```bash
history | tac
```

Shows the newest commands at the top.

---

## Practical Examples

### View Recent Command History

```bash
history | tac
```

---

### Recent SSH Activity

```bash
tac /var/log/auth.log | head -20
```

---

### Latest Nginx Errors

```bash
tac /var/log/nginx/error.log | head -30
```

---

### Latest Application Logs

```bash
tac application.log | less
```

---

## tac vs tail

| Command | Purpose                     |
| ------- | --------------------------- |
| `tail`  | Show last N lines           |
| `tac`   | Show entire file in reverse |

Example:

```bash
tail -10 app.log
```

Shows:

```text
Last 10 lines
```

Whereas:

```bash
tac app.log
```

Shows:

```text
Entire file reversed
```

---

## tac vs cat

| Feature       | cat       | tac       |
| ------------- | --------- | --------- |
| Normal order  | Yes       | No        |
| Reverse order | No        | Yes       |
| Small files   | Excellent | Excellent |
| Log analysis  | Limited   | Useful    |

---

## Common Interview Questions

### Q1. What is tac?

`tac` is the reverse version of `cat`.

---

### Q2. Why is it called tac?

Because it is simply:

```text
cat → tac
```

written backward.

---

### Q3. How do you view a file in reverse order?

```bash
tac file.txt
```

---

### Q4. How do you display recent log entries first?

```bash
tac app.log
```

---

### Q5. How do you show the newest 20 log entries?

```bash
tac app.log | head -20
```

---

## Related Commands

* cat
* less
* more
* head
* tail
* grep

---

## Notes

* `tac` is less commonly used than `cat`.
* Very useful for log analysis.
* Helps when newest information is at the bottom of a file.
* Often combined with `head`, `grep`, and `less`.

---

## References

```bash
man tac
info tac
```

---

## Quick Cheat Sheet

```bash
tac file.txt
tac app.log
tac app.log | less
tac app.log | grep ERROR
tac app.log | head -20
history | tac
```
