# column — Format Text into Tables

## Purpose

`column` formats text into neat columns and tables, making command output easier to read.

It is commonly used for:

* CSV viewing
* Log analysis
* Report generation
* Shell scripting
* Formatting command output

`column` does **not modify data**; it only changes how the output is displayed.

---

# Syntax

```bash
column [options]
```

Example:

```bash
cat data.txt | column -t
```

---

# Why Use column?

Without `column`:

```text
Name Age City
John 25 Delhi
Alice 30 Mumbai
Bob 28 Lucknow
```

Output looks messy.

With `column -t`:

```text
Name   Age  City
John   25   Delhi
Alice  30   Mumbai
Bob    28   Lucknow
```

Everything is aligned automatically.

---

# Common Options

| Option | Description          |
| ------ | -------------------- |
| `-t`   | Create table format  |
| `-s`   | Specify delimiter    |
| `-n`   | Do not merge columns |
| `-o`   | Output separator     |
| `-c`   | Set display width    |
| `-R`   | Right align columns  |

---

# Examples

## Example 1: Basic Table Formatting

File:

```text
John 25 Delhi
Alice 30 Mumbai
Bob 28 Lucknow
```

Command:

```bash
column -t employees.txt
```

Output:

```text
John   25  Delhi
Alice  30  Mumbai
Bob    28  Lucknow
```

---

## Example 2: Using Pipe

```bash
cat employees.txt | column -t
```

Output:

```text
John   25  Delhi
Alice  30  Mumbai
Bob    28  Lucknow
```

---

# CSV Formatting

File:

```csv
ID,Name,Salary
1,John,50000
2,Alice,70000
3,Bob,60000
```

---

## Example 3: Display CSV as Table

```bash
column -s ',' -t employees.csv
```

Output:

```text
ID  Name   Salary
1   John   50000
2   Alice  70000
3   Bob    60000
```

---

## Example 4: Pretty Print CSV

```bash
cat employees.csv | column -s ',' -t
```

---

# Custom Delimiters

File:

```text
John:25:Developer
Alice:30:Manager
Bob:28:Engineer
```

Command:

```bash
column -s ':' -t employees.txt
```

Output:

```text
John   25  Developer
Alice  30  Manager
Bob    28  Engineer
```

---

# Working with /etc/passwd

Example:

```bash
cat /etc/passwd | column -s ':' -t
```

Output:

```text
root   x  0  0  root   /root       /bin/bash
user   x  1000 1000    /home/user  /bin/bash
```

Much easier to read than raw output.

---

# Working with Logs

## Example 5: Format Log Entries

File:

```text
2026-06-10 ERROR Database_Failed
2026-06-10 INFO Startup
2026-06-10 WARN Disk_Low
```

Command:

```bash
column -t logfile.txt
```

Output:

```text
2026-06-10  ERROR  Database_Failed
2026-06-10  INFO   Startup
2026-06-10  WARN   Disk_Low
```

---

# column with Other Commands

## Example 6: Format ls Output

```bash
ls -l | column -t
```

---

## Example 7: Format df Output

```bash
df -h | column -t
```

Output becomes more readable.

---

## Example 8: Format mount Information

```bash
mount | column -t
```

---

## Example 9: Format Environment Variables

```bash
env | column -s '=' -t
```

Output:

```text
HOME      /home/user
USER      aman
SHELL     /bin/bash
```

---

# Formatting Command Output

## Example 10: Package List

```bash
dpkg -l | column -t
```

Ubuntu/Debian systems.

---

## Example 11: Network Interfaces

```bash
ip addr | column -t
```

---

## Example 12: Process Information

```bash
ps -ef | column -t
```

---

# Right Alignment

## Example 13

```bash
column -R 2 -t file.txt
```

Right-aligns column 2.

Useful for numbers.

---

# Custom Output Separator

## Example 14

```bash
column -s ':' -o ' | ' -t employees.txt
```

Output:

```text
John  | 25 | Developer
Alice | 30 | Manager
Bob   | 28 | Engineer
```

---

# Real-World Examples

### View CSV Reports

```bash
column -s ',' -t report.csv
```

---

### Read /etc/passwd Easily

```bash
column -s ':' -t /etc/passwd
```

---

### Format Process Reports

```bash
ps -ef | column -t
```

---

### Format Disk Usage

```bash
df -h | column -t
```

---

### Display Environment Variables

```bash
env | column -s '=' -t
```

---

# column vs awk

| Command | Purpose           |
| ------- | ----------------- |
| column  | Formatting output |
| awk     | Processing data   |

Example:

```bash
awk '{print $1}' file.txt
column -t file.txt
```

---

# column vs cut

| Command | Purpose                |
| ------- | ---------------------- |
| cut     | Extract columns        |
| column  | Display columns neatly |

Example:

```bash
cut -d ':' -f1 /etc/passwd
column -s ':' -t /etc/passwd
```

---

# Common Interview Questions

### Q1. What does column do?

Formats text into aligned columns.

---

### Q2. How do you display a CSV file as a table?

```bash
column -s ',' -t file.csv
```

---

### Q3. What does `-t` mean?

Create table format.

---

### Q4. What does `-s` mean?

Specify field delimiter.

---

### Q5. Is column used for data processing?

No.

It is used only for formatting output.

---

# Related Commands

* cut
* awk
* sed
* paste
* tr
* sort
* uniq

---

# Notes

* Excellent for viewing CSV files.
* Frequently used in shell scripts and reports.
* Makes command output human-readable.
* Does not modify original files.

---

# References

```bash
man column
info column
```

---

# Quick Cheat Sheet

```bash
column -t file.txt

column -s ',' -t file.csv

column -s ':' -t file.txt

cat file.csv | column -s ',' -t

df -h | column -t

ps -ef | column -t

env | column -s '=' -t

column -R 2 -t file.txt

column -s ':' -o ' | ' -t file.txt
```
