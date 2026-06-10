# cut — Extract Columns from Text

## Purpose

`cut` is used to extract specific columns, fields, or characters from files and command output.

It is commonly used for:

* CSV processing
* Log analysis
* Extracting usernames
* Parsing configuration files
* Shell scripting
* Data filtering

`cut` is simple, fast, and efficient when working with structured text.

---

# Syntax

```bash
cut [options] file
```

Example:

```bash
cut -d ':' -f1 /etc/passwd
```

---

# Understanding cut

File:

```text
John:25:Developer
Alice:30:Manager
Bob:28:Engineer
```

Field Mapping:

```text
Field 1 = John
Field 2 = 25
Field 3 = Developer
```

Command:

```bash
cut -d ':' -f1 employees.txt
```

Output:

```text
John
Alice
Bob
```

---

# Common Options

| Option         | Description                               |
| -------------- | ----------------------------------------- |
| `-d`           | Delimiter                                 |
| `-f`           | Select field(s)                           |
| `-c`           | Select character positions                |
| `--complement` | Select everything except specified fields |
| `-s`           | Skip lines without delimiter              |

---

# Field Extraction

## Example 1: Extract First Field

File:

```text
John:25:Developer
Alice:30:Manager
Bob:28:Engineer
```

Command:

```bash
cut -d ':' -f1 employees.txt
```

Output:

```text
John
Alice
Bob
```

---

## Example 2: Extract Second Field

```bash
cut -d ':' -f2 employees.txt
```

Output:

```text
25
30
28
```

---

## Example 3: Extract Third Field

```bash
cut -d ':' -f3 employees.txt
```

Output:

```text
Developer
Manager
Engineer
```

---

## Example 4: Extract Multiple Fields

```bash
cut -d ':' -f1,3 employees.txt
```

Output:

```text
John:Developer
Alice:Manager
Bob:Engineer
```

---

## Example 5: Extract Range of Fields

```bash
cut -d ':' -f1-2 employees.txt
```

Output:

```text
John:25
Alice:30
Bob:28
```

---

# Character Extraction

File:

```text
LinuxUbuntu
```

---

## Example 6: First Five Characters

```bash
cut -c1-5 file.txt
```

Output:

```text
Linux
```

---

## Example 7: Specific Characters

```bash
cut -c1,3,5 file.txt
```

Output:

```text
Lnx
```

---

## Example 8: Characters from Position 6 Onwards

```bash
cut -c6- file.txt
```

Output:

```text
Ubuntu
```

---

# Working with CSV Files

File:

```csv
1,John,50000
2,Alice,70000
3,Bob,60000
```

---

## Example 9: Extract Names

```bash
cut -d ',' -f2 employees.csv
```

Output:

```text
John
Alice
Bob
```

---

## Example 10: Extract Salaries

```bash
cut -d ',' -f3 employees.csv
```

Output:

```text
50000
70000
60000
```

---

## Example 11: Extract Name and Salary

```bash
cut -d ',' -f2,3 employees.csv
```

Output:

```text
John,50000
Alice,70000
Bob,60000
```

---

# Working with /etc/passwd

Example line:

```text
root:x:0:0:root:/root:/bin/bash
```

---

## Example 12: List Usernames

```bash
cut -d ':' -f1 /etc/passwd
```

Output:

```text
root
daemon
bin
sys
```

---

## Example 13: Show User Shells

```bash
cut -d ':' -f7 /etc/passwd
```

Output:

```text
/bin/bash
/usr/sbin/nologin
```

---

## Example 14: Username and Home Directory

```bash
cut -d ':' -f1,6 /etc/passwd
```

Output:

```text
root:/root
user:/home/user
```

---

# Working with Logs

Log File:

```text
192.168.1.10 GET /index.html 200
192.168.1.11 GET /login.html 404
```

---

## Example 15: Extract IP Addresses

```bash
cut -d ' ' -f1 access.log
```

Output:

```text
192.168.1.10
192.168.1.11
```

---

## Example 16: Extract Status Codes

```bash
cut -d ' ' -f4 access.log
```

Output:

```text
200
404
```

---

# cut with Pipes

## Example 17: Show Logged-in Users

```bash
who | cut -d ' ' -f1
```

---

## Example 18: Show Filesystem Names

```bash
df -h | cut -d ' ' -f1
```

---

## Example 19: Show Process Owner

```bash
ps aux | cut -d ' ' -f1
```

---

# Skip Selected Fields

## Example 20

```bash
cut -d ':' -f1 --complement employees.txt
```

Output:

```text
25:Developer
30:Manager
28:Engineer
```

---

# Skip Lines Without Delimiter

## Example 21

```bash
cut -s -d ':' -f1 file.txt
```

Only processes lines containing `:`.

---

# Real-World Examples

### Extract Hostnames

```bash
hostnamectl | grep hostname | cut -d ':' -f2
```

---

### List Installed Shells

```bash
cat /etc/passwd | cut -d ':' -f7 | sort | uniq
```

---

### Extract Error Codes

```bash
grep ERROR app.log | cut -d ' ' -f5
```

---

### Show Running Commands

```bash
ps aux | awk '{print $11}' | cut -d '/' -f3
```

---

### Extract Domains

```bash
cut -d '@' -f2 emails.txt
```

Input:

```text
user1@gmail.com
user2@yahoo.com
```

Output:

```text
gmail.com
yahoo.com
```

---

# cut vs awk

| Command | Best Use                             |
| ------- | ------------------------------------ |
| `cut`   | Simple column extraction             |
| `awk`   | Advanced processing and calculations |

Example:

```bash
cut -d ':' -f1 file
awk -F ':' '{print $1}' file
```

Both produce similar output.

---

# cut vs grep

| Command | Purpose         |
| ------- | --------------- |
| grep    | Search          |
| cut     | Extract columns |

Example:

```bash
grep ERROR app.log
cut -d ' ' -f4 app.log
```

---

# Common Interview Questions

### Q1. What is cut used for?

Extracting fields or characters from text.

---

### Q2. What does `-d` do?

Specifies the delimiter.

Example:

```bash
cut -d ':' -f1 file
```

---

### Q3. What does `-f` do?

Selects field numbers.

---

### Q4. What does `-c` do?

Selects character positions.

---

### Q5. How do you extract usernames from `/etc/passwd`?

```bash
cut -d ':' -f1 /etc/passwd
```

---

# Related Commands

* awk
* grep
* sed
* sort
* uniq
* paste
* tr

---

# Notes

* `cut` is faster than `awk` for simple field extraction.
* Best for structured text.
* Frequently used with pipes.
* Commonly used in shell scripts and automation.

---

# References

```bash
man cut
info cut
```

---

# Quick Cheat Sheet

```bash
cut -d ':' -f1 file

cut -d ':' -f2 file

cut -d ':' -f1,3 file

cut -d ':' -f1-3 file

cut -c1-5 file

cut -c6- file

cut -d ',' -f2 employees.csv

cut -d ':' -f1 /etc/passwd

cut -d ' ' -f1 access.log

cut -s -d ':' -f1 file
```
