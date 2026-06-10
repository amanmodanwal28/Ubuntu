# awk — Pattern Scanning and Text Processing

## Purpose

`awk` is one of the most powerful text-processing tools in Linux.

It reads input line by line, splits each line into fields (columns), and performs operations on those fields.

`awk` is commonly used for:

* Extracting columns
* Processing CSV files
* Generating reports
* Filtering data
* Log analysis
* Data calculations

Think of `awk` as a mini programming language built into Linux.

---

## Syntax

```bash
awk 'pattern { action }' file
```

Example:

```bash
awk '{print $1}' employees.txt
```

---

## Understanding Fields

File:

```text
John 25 Developer
Alice 30 Manager
Bob 28 Engineer
```

Field Mapping:

```text
$1 = John
$2 = 25
$3 = Developer
```

Special Variables:

| Variable | Description            |
| -------- | ---------------------- |
| `$0`     | Entire line            |
| `$1`     | First field            |
| `$2`     | Second field           |
| `$3`     | Third field            |
| `NF`     | Number of fields       |
| `NR`     | Current line number    |
| `FS`     | Input field separator  |
| `OFS`    | Output field separator |

---

# Common Commands

| Command                                | Description          |
| -------------------------------------- | -------------------- |
| `awk '{print $1}' file`                | Print first column   |
| `awk '{print $NF}' file`               | Print last column    |
| `awk '{print NR,$0}' file`             | Show line numbers    |
| `awk 'NR==5' file`                     | Print line 5         |
| `awk 'NR<=10' file`                    | Print first 10 lines |
| `awk '/ERROR/' file`                   | Search pattern       |
| `awk '$3 > 100' file`                  | Numeric comparison   |
| `awk -F ',' '{print $1}' file.csv`     | CSV processing       |
| `awk '{sum+=$2} END {print sum}' file` | Calculate total      |
| `awk '{print toupper($1)}' file`       | Convert to uppercase |

---

# Examples

## Example 1: Print First Column

```bash
awk '{print $1}' employees.txt
```

Output:

```text
John
Alice
Bob
```

---

## Example 2: Print Multiple Columns

```bash
awk '{print $1,$3}' employees.txt
```

Output:

```text
John Developer
Alice Manager
Bob Engineer
```

---

## Example 3: Print Last Column

```bash
awk '{print $NF}' employees.txt
```

Output:

```text
Developer
Manager
Engineer
```

---

## Example 4: Show Line Numbers

```bash
awk '{print NR,$0}' employees.txt
```

Output:

```text
1 John 25 Developer
2 Alice 30 Manager
3 Bob 28 Engineer
```

---

## Example 5: Print Specific Line

```bash
awk 'NR==2' employees.txt
```

Output:

```text
Alice 30 Manager
```

---

## Example 6: Print First 5 Lines

```bash
awk 'NR<=5' file.txt
```

---

## Example 7: Search Pattern

```bash
awk '/ERROR/' app.log
```

Output:

```text
ERROR Database Failed
ERROR Connection Timeout
```

---

# CSV Processing

File:

```csv
ID,Name,Salary
1,John,50000
2,Alice,70000
3,Bob,60000
```

---

## Example 8: Extract Names

```bash
awk -F ',' '{print $2}' employees.csv
```

Output:

```text
Name
John
Alice
Bob
```

---

## Example 9: Name and Salary

```bash
awk -F ',' '{print $2,$3}' employees.csv
```

Output:

```text
John 50000
Alice 70000
Bob 60000
```

---

# Calculations

## Example 10: Sum a Column

File:

```text
John 5000
Alice 6000
Bob 7000
```

Command:

```bash
awk '{sum+=$2} END {print sum}' salary.txt
```

Output:

```text
18000
```

---

## Example 11: Average

```bash
awk '{sum+=$2} END {print sum/NR}' salary.txt
```

Output:

```text
6000
```

---

## Example 12: Maximum Value

```bash
awk 'max<$2{max=$2} END{print max}' salary.txt
```

Output:

```text
7000
```

---

# Filtering Data

## Example 13: Salary Greater Than 60000

```bash
awk -F ',' '$3 > 60000' employees.csv
```

Output:

```text
2,Alice,70000
```

---

## Example 14: Show Only Developers

```bash
awk '$3=="Developer"' employees.txt
```

Output:

```text
John 25 Developer
```

---

# Log Analysis

## Example 15: Find Errors

```bash
awk '/ERROR/' app.log
```

---

## Example 16: Count Errors

```bash
awk '/ERROR/{count++} END{print count}' app.log
```

---

## Example 17: Extract IP Addresses

```bash
awk '{print $1}' access.log
```

Output:

```text
192.168.1.10
192.168.1.11
192.168.1.12
```

---

# BEGIN and END Blocks

```bash
awk '
BEGIN {print "Report Started"}
{print $1}
END {print "Report Finished"}
' file.txt
```

Output:

```text
Report Started
John
Alice
Bob
Report Finished
```

---

# awk with Pipes

## Show Running Processes

```bash
ps aux | awk '{print $1,$11}'
```

---

## Show Disk Usage

```bash
df -h | awk '{print $1,$5}'
```

---

## Show Memory Usage

```bash
free -h | awk '/Mem/ {print $2,$3,$4}'
```

Output:

```text
8Gi 3Gi 5Gi
```

---

# awk vs grep vs sed

| Tool   | Purpose                  |
| ------ | ------------------------ |
| `grep` | Search text              |
| `sed`  | Replace/edit text        |
| `awk`  | Process columns and data |

Example:

```bash
grep ERROR app.log
sed 's/error/warning/' file.txt
awk '{print $1}' file.txt
```

---

# Common Interview Questions

### Q1. What is awk?

A text-processing and reporting tool used to manipulate structured text data.

### Q2. What does `$1` mean?

The first field (column).

### Q3. What does `$0` mean?

The entire line.

### Q4. What does `NR` mean?

Current line number.

### Q5. What does `NF` mean?

Number of fields in the current line.

### Q6. How do you process CSV files?

```bash
awk -F ',' '{print $1}' file.csv
```

---

# Real-World Examples

### Display Usernames

```bash
awk -F ':' '{print $1}' /etc/passwd
```

### Show Running Commands

```bash
ps aux | awk '{print $11}'
```

### Disk Usage Report

```bash
df -h | awk '{print $1,$5}'
```

### Memory Usage

```bash
free -h | awk '/Mem/ {print $2,$3,$4}'
```

### Count Application Errors

```bash
awk '/ERROR/{count++} END{print count}' app.log
```

---

# Related Commands

* grep
* sed
* cut
* sort
* uniq
* wc

---

# Notes

* `awk` is one of the most important Linux text-processing commands.
* Extremely useful for DevOps, Embedded Linux, System Administration, and Automation.
* Supports variables, conditions, loops, calculations, and formatting.
* Works best with structured text data.

---

# References

```bash
man awk
info awk
```

---

# Quick Cheat Sheet

```bash
awk '{print $1}' file
awk '{print $NF}' file
awk '{print NR,$0}' file
awk 'NR==5' file
awk '/ERROR/' app.log

awk -F ',' '{print $1}' file.csv

awk '{sum+=$2} END {print sum}' file
awk '{sum+=$2} END {print sum/NR}' file

ps aux | awk '{print $1,$11}'
df -h | awk '{print $1,$5}'
free -h | awk '/Mem/ {print $2,$3,$4}'
```
