# sed — Stream Editor

## Purpose

`sed` (Stream Editor) is a powerful Linux command used to:

* Search text
* Replace text
* Delete lines
* Insert text
* Modify files automatically
* Process large text streams

Unlike text editors such as `vim` or `nano`, `sed` works directly from the command line.

It is commonly used in:

* Shell scripts
* Log processing
* Configuration management
* DevOps automation
* Embedded Linux

---

## Syntax

```bash
sed [options] 'command' file
```

Example:

```bash
sed 's/Linux/Ubuntu/' file.txt
```

---

# Understanding sed

Suppose a file contains:

```text
I love Linux
Linux is powerful
Linux is open source
```

Command:

```bash
sed 's/Linux/Ubuntu/' file.txt
```

Output:

```text
I love Ubuntu
Ubuntu is powerful
Ubuntu is open source
```

---

# Common Commands

| Command                         | Description              |
| ------------------------------- | ------------------------ |
| `sed 's/old/new/' file`         | Replace first occurrence |
| `sed 's/old/new/g' file`        | Replace all occurrences  |
| `sed -i 's/old/new/g' file`     | Edit file permanently    |
| `sed -n '5p' file`              | Print line 5             |
| `sed -n '5,10p' file`           | Print lines 5-10         |
| `sed '5d' file`                 | Delete line 5            |
| `sed '/ERROR/d' file`           | Delete matching lines    |
| `sed -n '/ERROR/p' file`        | Print matching lines     |
| `sed '$d' file`                 | Delete last line         |
| `sed '1d' file`                 | Delete first line        |
| `sed -n '1,10p' file`           | Print first 10 lines     |
| `sed -i '/pattern/a text' file` | Append after match       |
| `sed -i '/pattern/i text' file` | Insert before match      |

---

# Examples

## Example 1: Replace Text

File:

```text
Linux is awesome
```

Command:

```bash
sed 's/Linux/Ubuntu/' file.txt
```

Output:

```text
Ubuntu is awesome
```

---

## Example 2: Replace All Occurrences

File:

```text
Linux Linux Linux
```

Command:

```bash
sed 's/Linux/Ubuntu/g' file.txt
```

Output:

```text
Ubuntu Ubuntu Ubuntu
```

---

## Example 3: Edit File Permanently

```bash
sed -i 's/localhost/192.168.1.10/g' config.conf
```

Updates the file directly.

---

## Example 4: Print Specific Line

```bash
sed -n '5p' file.txt
```

Displays only line 5.

---

## Example 5: Print Line Range

```bash
sed -n '10,20p' file.txt
```

Displays lines 10 through 20.

---

## Example 6: Delete Line

```bash
sed '5d' file.txt
```

Deletes line 5 from output.

---

## Example 7: Delete Matching Lines

```bash
sed '/ERROR/d' app.log
```

Removes all lines containing ERROR.

---

## Example 8: Delete Blank Lines

```bash
sed '/^$/d' file.txt
```

Removes empty lines.

---

## Example 9: Delete Comments

```bash
sed '/^#/d' config.conf
```

Removes comment lines.

---

# Insert and Append Text

## Example 10: Append After Match

```bash
sed '/server/a listen=8080' config.conf
```

Input:

```text
server
```

Output:

```text
server
listen=8080
```

---

## Example 11: Insert Before Match

```bash
sed '/server/i # Web Server Config' config.conf
```

Output:

```text
# Web Server Config
server
```

---

# Multiple Replacements

## Example 12

```bash
sed -e 's/red/blue/g' -e 's/green/yellow/g' file.txt
```

Performs multiple replacements.

---

# Working with Logs

## Example 13: Show Errors Only

```bash
sed -n '/ERROR/p' app.log
```

---

## Example 14: Remove INFO Messages

```bash
sed '/INFO/d' app.log
```

---

## Example 15: Replace IP Address

```bash
sed 's/192.168.1.100/192.168.1.200/g' app.log
```

---

# CSV Processing

File:

```csv
1,John,50000
2,Alice,70000
3,Bob,60000
```

---

## Example 16: Replace Delimiter

```bash
sed 's/,/ | /g' employees.csv
```

Output:

```text
1 | John | 50000
2 | Alice | 70000
3 | Bob | 60000
```

---

# sed with Pipes

## Example 17: Process Command Output

```bash
df -h | sed 's/%//g'
```

Removes percentage signs.

---

## Example 18: Format Memory Output

```bash
free -h | sed -n '2p'
```

Displays memory information.

---

## Example 19: Modify Process Output

```bash
ps aux | sed -n '1,5p'
```

Displays first 5 lines.

---

# Regular Expressions

## Lines Starting with Root

```bash
sed -n '/^root/p' /etc/passwd
```

---

## Lines Ending with Bash

```bash
sed -n '/bash$/p' /etc/passwd
```

---

## Lines Containing Numbers

```bash
sed -n '/[0-9]/p' file.txt
```

---

# sed vs grep vs awk

| Tool | Purpose              |
| ---- | -------------------- |
| grep | Search text          |
| sed  | Modify text          |
| awk  | Process columns/data |

Example:

```bash
grep ERROR app.log
sed 's/error/warning/g' app.log
awk '{print $1}' file.txt
```

---

# Common Interview Questions

### Q1. What is sed?

A stream editor used for searching, replacing, inserting, deleting, and editing text.

---

### Q2. What does `s` mean in sed?

Substitute.

Example:

```bash
sed 's/old/new/'
```

---

### Q3. What does `g` mean?

Global replacement.

```bash
sed 's/old/new/g'
```

Replaces all occurrences.

---

### Q4. What does `-i` do?

Modifies the file directly.

```bash
sed -i 's/old/new/g' file.txt
```

---

### Q5. How do you print line 10?

```bash
sed -n '10p' file.txt
```

---

# Real-World Examples

### Update Configuration

```bash
sed -i 's/PORT=8080/PORT=9090/' .env
```

---

### Remove Comments

```bash
sed '/^#/d' config.conf
```

---

### Delete Blank Lines

```bash
sed '/^$/d' file.txt
```

---

### Replace Hostname

```bash
sed -i 's/server-old/server-new/g' inventory.txt
```

---

### Extract Errors

```bash
sed -n '/ERROR/p' app.log
```

---

# Related Commands

* grep
* awk
* cut
* sort
* uniq
* tr

---

# Notes

* `sed` is one of the most important Linux text-processing commands.
* Commonly used in automation scripts.
* Excellent for search-and-replace operations.
* Works efficiently on large files.
* Frequently used with `grep` and `awk`.

---

# References

```bash
man sed
info sed
```

---

# Quick Cheat Sheet

```bash
sed 's/old/new/' file
sed 's/old/new/g' file
sed -i 's/old/new/g' file

sed -n '5p' file
sed -n '5,10p' file

sed '5d' file
sed '/ERROR/d' file

sed '/^#/d' config.conf
sed '/^$/d' file.txt

sed '/pattern/a text' file
sed '/pattern/i text' file
```
