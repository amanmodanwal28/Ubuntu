# paste — Merge Lines of Files

## Purpose

`paste` combines lines from multiple files horizontally (side-by-side).

Unlike `cat`, which joins files vertically, `paste` joins corresponding lines into a single output line.

It is commonly used for:

* CSV generation
* Combining reports
* Data processing
* Log analysis
* Shell scripting
* Merging columns

---

# Syntax

```bash
paste [options] file1 file2
```

Example:

```bash
paste names.txt ages.txt
```

---

# Understanding paste

File: names.txt

```text
John
Alice
Bob
```

File: ages.txt

```text
25
30
28
```

Command:

```bash
paste names.txt ages.txt
```

Output:

```text
John    25
Alice   30
Bob     28
```

By default, `paste` uses TAB as separator.

---

# Common Options

| Option                     | Description                   |
| -------------------------- | ----------------------------- |
| `paste file1 file2`        | Merge files side-by-side      |
| `paste -d ',' file1 file2` | Use comma delimiter           |
| `paste -d ':' file1 file2` | Use colon delimiter           |
| `paste -s file`            | Merge all lines into one line |
| `paste -s -d ',' file`     | Create CSV-style output       |

---

# Examples

## Example 1: Merge Two Files

names.txt

```text
John
Alice
Bob
```

ages.txt

```text
25
30
28
```

Command:

```bash
paste names.txt ages.txt
```

Output:

```text
John    25
Alice   30
Bob     28
```

---

## Example 2: Merge Three Files

names.txt

```text
John
Alice
Bob
```

ages.txt

```text
25
30
28
```

city.txt

```text
Delhi
Mumbai
Lucknow
```

Command:

```bash
paste names.txt ages.txt city.txt
```

Output:

```text
John    25    Delhi
Alice   30    Mumbai
Bob     28    Lucknow
```

---

# Custom Delimiters

## Example 3: CSV Output

```bash
paste -d ',' names.txt ages.txt
```

Output:

```text
John,25
Alice,30
Bob,28
```

---

## Example 4: Colon Separator

```bash
paste -d ':' names.txt ages.txt
```

Output:

```text
John:25
Alice:30
Bob:28
```

---

## Example 5: Multiple Delimiters

```bash
paste -d ':,' file1 file2 file3
```

Output:

```text
John:25,Delhi
Alice:30,Mumbai
Bob:28,Lucknow
```

---

# Serial Mode

Normally:

```bash
paste file.txt
```

Input:

```text
Linux
Ubuntu
Debian
Fedora
```

Output:

```text
Linux
Ubuntu
Debian
Fedora
```

---

## Example 6: Single Line Output

```bash
paste -s file.txt
```

Output:

```text
Linux    Ubuntu    Debian    Fedora
```

---

## Example 7: CSV Line

```bash
paste -s -d ',' file.txt
```

Output:

```text
Linux,Ubuntu,Debian,Fedora
```

---

# Working with Command Output

## Example 8: Merge Usernames and UIDs

```bash
cut -d ':' -f1 /etc/passwd > users.txt
cut -d ':' -f3 /etc/passwd > uid.txt

paste users.txt uid.txt
```

Output:

```text
root      0
daemon    1
user      1000
```

---

## Example 9: Combine Hostname and Date

```bash
paste <(hostname) <(date)
```

Output:

```text
ubuntu-pc    Wed Jun 10 12:00:00 IST 2026
```

---

# Creating CSV Files

## Example 10

names.txt

```text
John
Alice
Bob
```

salary.txt

```text
50000
70000
60000
```

Command:

```bash
paste -d ',' names.txt salary.txt > employees.csv
```

Output:

```csv
John,50000
Alice,70000
Bob,60000
```

---

# Log Analysis

## Example 11

Merge timestamps with messages:

time.txt

```text
10:00
10:05
10:10
```

msg.txt

```text
START
RUNNING
STOP
```

Command:

```bash
paste time.txt msg.txt
```

Output:

```text
10:00    START
10:05    RUNNING
10:10    STOP
```

---

# Shell Script Examples

## Example 12

Generate report:

```bash
paste users.txt memory.txt cpu.txt
```

Output:

```text
user1   500MB   20%
user2   800MB   35%
user3   300MB   10%
```

---

## Example 13

Create Inventory Report

```bash
paste products.txt quantity.txt price.txt
```

Output:

```text
Mouse      20    500
Keyboard   15    1000
Monitor    10    12000
```

---

# Real-World Examples

### Create CSV from Multiple Files

```bash
paste -d ',' names.txt salary.txt city.txt
```

---

### Merge IP and Hostname Lists

```bash
paste ip.txt hosts.txt
```

---

### Generate User Report

```bash
paste usernames.txt groups.txt
```

---

### Merge Two Logs

```bash
paste timestamps.log events.log
```

---

### Convert Lines to CSV

```bash
paste -s -d ',' file.txt
```

---

# paste vs cat

| Command | Purpose          |
| ------- | ---------------- |
| cat     | Vertical merge   |
| paste   | Horizontal merge |

Example:

```bash
cat file1 file2
```

Output:

```text
file1 contents
file2 contents
```

---

```bash
paste file1 file2
```

Output:

```text
line1_file1    line1_file2
line2_file1    line2_file2
```

---

# paste vs join

| Command | Purpose                 |
| ------- | ----------------------- |
| paste   | Merge by line number    |
| join    | Merge by matching field |

Example:

```bash
paste file1 file2
join file1 file2
```

---

# Common Interview Questions

### Q1. What does paste do?

Combines files horizontally line-by-line.

---

### Q2. What is the default delimiter?

TAB character.

---

### Q3. How do you create CSV output?

```bash
paste -d ',' file1 file2
```

---

### Q4. What does `-s` do?

Serial mode.

Converts multiple lines into one line.

---

### Q5. Difference between cat and paste?

`cat` joins vertically.

`paste` joins horizontally.

---

# Related Commands

* cat
* cut
* awk
* sed
* tr
* join
* column

---

# Notes

* Useful for CSV creation.
* Frequently used with `cut`.
* Great for report generation.
* Works line-by-line.

---

# References

```bash
man paste
info paste
```

---

# Quick Cheat Sheet

```bash
paste file1 file2

paste file1 file2 file3

paste -d ',' file1 file2

paste -d ':' file1 file2

paste -s file.txt

paste -s -d ',' file.txt

paste users.txt groups.txt

paste names.txt salaries.txt > report.txt

paste <(hostname) <(date)
```
