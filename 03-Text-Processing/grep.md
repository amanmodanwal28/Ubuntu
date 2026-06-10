# grep — Search Text Patterns

## Purpose

`grep` stands for **Global Regular Expression Print**.

It is one of the most powerful Linux commands used to search for text patterns inside:

* Files
* Log files
* Command output
* Source code
* Configuration files

`grep` prints only the lines that match the specified pattern.

---

## Syntax

```bash
grep [options] "pattern" file
```

Example:

```bash
grep "error" app.log
```

---

## Common Commands

| Command                    | Description               |
| -------------------------- | ------------------------- |
| `grep 'pattern' file`      | Basic search              |
| `grep -i 'pattern' file`   | Ignore case               |
| `grep -n 'pattern' file`   | Show line numbers         |
| `grep -v 'pattern' file`   | Show non-matching lines   |
| `grep -c 'pattern' file`   | Count matches             |
| `grep -w 'word' file`      | Exact word match          |
| `grep -r 'pattern' dir/`   | Recursive search          |
| `grep -l 'pattern' dir/`   | Show filenames only       |
| `grep -A 3 'pattern' file` | Show 3 lines after match  |
| `grep -B 3 'pattern' file` | Show 3 lines before match |
| `grep -C 3 'pattern' file` | Show context around match |
| `grep -E 'p1\|p2' file`    | Multiple patterns         |
| `grep -o 'pattern' file`   | Print matched text only   |
| `grep -q 'pattern' file`   | Quiet mode                |
| `grep -m 5 'pattern' file` | Stop after 5 matches      |

---

## Examples

### Example 1: Basic Search

```bash
grep "error" app.log
```

Output:

```text
ERROR: Database Connection Failed
ERROR: Timeout Occurred
```

---

### Example 2: Case-Insensitive Search

```bash
grep -i "error" app.log
```

Matches:

```text
error
Error
ERROR
```

---

### Example 3: Show Line Numbers

```bash
grep -n "error" app.log
```

Output:

```text
12: ERROR Database Failed
45: ERROR Connection Timeout
```

---

### Example 4: Count Matches

```bash
grep -c "404" access.log
```

Output:

```text
25
```

Shows how many matching lines exist.

---

### Example 5: Exact Word Match

```bash
grep -w "port" nginx.conf
```

Matches:

```text
port
```

Does NOT match:

```text
ports
transport
```

---

### Example 6: Inverse Search

```bash
grep -v "#" config.conf
```

Displays all non-comment lines.

---

### Example 7: Recursive Search

```bash
grep -rn "TODO" .
```

Output:

```text
./main.py:12: TODO Fix Login
./api.py:45: TODO Add Validation
```

---

### Example 8: Multiple Patterns

```bash
grep -E "ERROR|WARN" app.log
```

Output:

```text
ERROR Database Failed
WARN Memory High
```

---

## Common Use Cases

### 1. Find Errors in Logs

```bash
grep -i "error" app.log
```

Very common in production troubleshooting.

---

### 2. Search Warnings

```bash
grep -i "warn" app.log
```

---

### 3. Search Source Code

```bash
grep -rn "connect()" src/
```

Find function usage in code.

---

### 4. Verify Configuration

```bash
grep "listen" nginx.conf
```

Check web server port configuration.

---

### 5. Remove Comments

```bash
grep -v "^#" config.conf
```

Shows active configuration only.

---

### 6. Count HTTP Errors

```bash
grep -c "404" access.log
```

Count failed requests.

---

### 7. Check Running Process

```bash
ps aux | grep nginx
```

Output:

```text
root  1234 nginx
```

---

### 8. Search SSH Configuration

```bash
grep "PermitRootLogin" /etc/ssh/sshd_config
```

---

### 9. Find TODO Comments

```bash
grep -rn "TODO" .
```

Useful during development.

---

### 10. Search IP Addresses

```bash
grep "192.168" network.log
```

---

### 11. Find Password References

```bash
grep -rl "password" .
```

Shows filenames only.

---

### 12. Search Environment Variables

```bash
grep "PORT" .env
```

---

## Context Search

### Show 3 Lines After Match

```bash
grep -A 3 "Exception" error.log
```

Output:

```text
Exception Found
Stack Line 1
Stack Line 2
Stack Line 3
```

---

### Show 3 Lines Before Match

```bash
grep -B 3 "Exception" error.log
```

---

### Show Complete Context

```bash
grep -C 3 "Exception" error.log
```

Most useful for debugging.

---

## grep with Pipes

### Find Running SSH Process

```bash
ps aux | grep ssh
```

---

### Search Open Ports

```bash
netstat -tulpn | grep 80
```

---

### Search Memory Usage

```bash
free -h | grep Mem
```

---

### Filter Logs

```bash
cat app.log | grep ERROR
```

Better:

```bash
grep ERROR app.log
```

---

### Multiple Filters

```bash
cat access.log | grep 500 | grep -v healthcheck
```

Output:

```text
500 Internal Server Error
```

---

## Regular Expression Examples

### Starts With

```bash
grep "^root" /etc/passwd
```

---

### Ends With

```bash
grep "bash$" /etc/passwd
```

---

### Digits

```bash
grep "[0-9]" file.txt
```

---

### Multiple Characters

```bash
grep "[abc]" file.txt
```

Matches lines containing a, b, or c.

---

## grep vs find

| Command | Purpose                  |
| ------- | ------------------------ |
| grep    | Search inside files      |
| find    | Search files/directories |

Example:

```bash
find . -name "*.log"
```

Finds files.

```bash
grep "ERROR" app.log
```

Finds text inside files.

---

## grep vs awk vs sed

| Tool | Purpose        |
| ---- | -------------- |
| grep | Search         |
| sed  | Replace/Edit   |
| awk  | Process Fields |

Example:

```bash
grep ERROR app.log
sed 's/error/warning/' file.txt
awk '{print $1}' file.txt
```

---

## Common Interview Questions

### Q1. What does grep stand for?

Global Regular Expression Print.

---

### Q2. How do you search recursively?

```bash
grep -rn "TODO" .
```

---

### Q3. How do you ignore case?

```bash
grep -i "error" app.log
```

---

### Q4. How do you count matches?

```bash
grep -c "404" access.log
```

---

### Q5. How do you search multiple patterns?

```bash
grep -E "ERROR|WARN" app.log
```

---

## Practical Examples

### Application Logs

```bash
grep ERROR app.log
```

### Nginx Logs

```bash
grep 404 access.log
```

### Source Code

```bash
grep -rn "main()" src/
```

### SSH Configuration

```bash
grep PermitRootLogin /etc/ssh/sshd_config
```

### Running Processes

```bash
ps aux | grep nginx
```

---

## Related Commands

* find
* sed
* awk
* cut
* sort
* uniq

---

## Notes

* `grep` is one of the most used Linux commands.
* Essential for log analysis and debugging.
* Works extremely well with pipes (`|`).
* Supports regular expressions.
* Commonly used by Linux Admins, DevOps Engineers, Embedded Developers, and Software Engineers.

---

## References

```bash
man grep
info grep
```

---

## Quick Cheat Sheet

```bash
grep "error" app.log
grep -i "error" app.log
grep -n "error" app.log
grep -v "#" config.conf
grep -c "404" access.log
grep -rn "TODO" .
grep -E "ERROR|WARN" app.log
grep -A 3 "Exception" error.log
grep -B 3 "Exception" error.log
grep -C 3 "Exception" error.log
ps aux | grep nginx
```
