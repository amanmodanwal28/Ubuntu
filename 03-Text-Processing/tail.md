# tail — View the End of a File

## Purpose

The `tail` command displays the last lines of a file.

By default, it shows the **last 10 lines**.

It is one of the most important Linux commands for:

* Log monitoring
* Troubleshooting
* Real-time application monitoring
* System administration

The most powerful feature of `tail` is the `-f` option, which allows you to watch a file as new data is added.

---

## Syntax

```bash
tail [options] file_name
```

Example:

```bash
tail application.log
```

---

## Common Commands

| Command                   | Description                     |
| ------------------------- | ------------------------------- |
| `tail file.txt`           | Show last 10 lines              |
| `tail -n 50 file.txt`     | Show last 50 lines              |
| `tail -n 100 file.txt`    | Show last 100 lines             |
| `tail -n +5 file.txt`     | Show from line 5 to end         |
| `tail -f file.txt`        | Follow file in real time        |
| `tail -F file.txt`        | Follow file even after rotation |
| `tail -f -n 100 file.txt` | Show last 100 lines then follow |

---

## Examples

### Example 1: Show Last 10 Lines

```bash
tail app.log
```

Output:

```text
[INFO] Started
[INFO] Connected
[ERROR] Timeout
...
```

Displays the most recent entries.

---

### Example 2: Show Last 50 Lines

```bash
tail -n 50 app.log
```

Useful when the log file is large.

---

### Example 3: Show Last 100 Lines

```bash
tail -n 100 app.log
```

Common for troubleshooting applications.

---

### Example 4: Start from Line 5

```bash
tail -n +5 file.txt
```

Input:

```text
1 Linux
2 Ubuntu
3 Debian
4 Fedora
5 Arch
6 Kali
```

Output:

```text
Arch
Kali
```

Shows from line 5 to the end.

---

### Example 5: Follow a Log File

```bash
tail -f app.log
```

Output:

```text
[INFO] Server Started
```

Later:

```text
[INFO] User Login
[ERROR] Database Timeout
```

New lines appear automatically.

Exit:

```text
Ctrl + C
```

---

### Example 6: Follow with Log Rotation Support

```bash
tail -F app.log
```

Useful when:

```text
app.log
app.log.1
app.log.2
```

are rotated by log management tools.

---

## Common Use Cases

### 1. Monitor Application Logs

```bash
tail -f application.log
```

Most common developer use case.

---

### 2. Monitor System Logs

Ubuntu:

```bash
tail -f /var/log/syslog
```

RHEL/CentOS:

```bash
tail -f /var/log/messages
```

---

### 3. Monitor Nginx Access Logs

```bash
tail -f /var/log/nginx/access.log
```

View incoming requests in real time.

---

### 4. Monitor Nginx Error Logs

```bash
tail -f /var/log/nginx/error.log
```

Useful for debugging web servers.

---

### 5. Monitor Apache Logs

```bash
tail -f /var/log/apache2/access.log
```

---

### 6. Watch Docker Container Logs

```bash
docker logs -f container_name
```

Internally behaves similar to `tail -f`.

---

### 7. View Recent SSH Activity

```bash
tail -f /var/log/auth.log
```

Shows login attempts.

---

### 8. Monitor Embedded Linux Systems

```bash
tail -f /var/log/messages
```

Very common in embedded development.

---

## Real-Time Error Monitoring

### Show Only Errors

```bash
tail -f app.log | grep --line-buffered ERROR
```

Output:

```text
ERROR Database Connection Failed
ERROR Authentication Failed
```

Displays errors only.

---

### Show Warnings

```bash
tail -f app.log | grep --line-buffered WARN
```

Useful for production monitoring.

---

## Multiple Files

Monitor multiple files:

```bash
tail -f app.log nginx.log
```

Output:

```text
==> app.log <==
Application Started

==> nginx.log <==
GET /index.html
```

Useful when troubleshooting several services.

---

## tail vs head

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

## tail vs cat

| Feature           | tail      | cat  |
| ----------------- | --------- | ---- |
| Last lines only   | Yes       | No   |
| Real-time follow  | Yes       | No   |
| Large log support | Excellent | Poor |
| Monitoring        | Yes       | No   |

Example:

```bash
tail -f app.log
```

is much better than:

```bash
cat app.log
```

for logs.

---

## tail vs less

| Feature              | tail      | less    |
| -------------------- | --------- | ------- |
| Real-time monitoring | Excellent | Limited |
| Search               | No        | Yes     |
| Interactive browsing | No        | Yes     |
| Log monitoring       | Excellent | Good    |

---

## Common Interview Questions

### Q1. What does tail do?

Displays the last lines of a file.

---

### Q2. How many lines does tail show by default?

```text
10 lines
```

---

### Q3. What does `tail -f` do?

Follows a file in real time and displays newly added lines.

---

### Q4. Difference between `tail -f` and `tail -F`?

| Option | Meaning                             |
| ------ | ----------------------------------- |
| `-f`   | Follow file                         |
| `-F`   | Follow file and handle log rotation |

---

### Q5. How do you display the last 100 lines?

```bash
tail -n 100 app.log
```

---

## Practical Examples

### Application Logs

```bash
tail -f app.log
```

---

### System Logs

```bash
tail -f /var/log/syslog
```

---

### Authentication Logs

```bash
tail -f /var/log/auth.log
```

---

### Nginx Access Logs

```bash
tail -f /var/log/nginx/access.log
```

---

### Last 50 Lines

```bash
tail -n 50 app.log
```

---

### Error Monitoring

```bash
tail -f app.log | grep --line-buffered ERROR
```

---

## Related Commands

* head
* cat
* less
* more
* grep
* journalctl
* dmesg

---

## Notes

* `tail -f` is one of the most important Linux commands.
* Essential for developers, DevOps engineers, and system administrators.
* Commonly used for monitoring logs in production systems.
* Combine with `grep` for real-time filtering.
* Use `tail -F` when log rotation is enabled.

---

## References

```bash
man tail
info tail
```

---

## Quick Cheat Sheet

```bash
tail file.txt
tail -n 50 file.txt
tail -n 100 file.txt
tail -n +5 file.txt

tail -f app.log
tail -F app.log

tail -f /var/log/syslog
tail -f /var/log/nginx/access.log

tail -f app.log | grep ERROR
```
