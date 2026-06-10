# sort — Sort Lines of Text Files

## Purpose

The `sort` command is used to sort lines of text files alphabetically, numerically, or according to specific fields.

It is commonly used for:

* Log analysis
* Data processing
* CSV file sorting
* Report generation
* Removing duplicates (with `uniq`)
* Shell scripting

`sort` reads input line by line and outputs the lines in sorted order.

---

## Syntax

```bash
sort [options] file
```

Example:

```bash
sort names.txt
```

---

# Common Commands

| Command                    | Description                    |
| -------------------------- | ------------------------------ |
| `sort file.txt`            | Sort alphabetically            |
| `sort -r file.txt`         | Reverse sort                   |
| `sort -n file.txt`         | Numeric sort                   |
| `sort -u file.txt`         | Sort and remove duplicates     |
| `sort -k2 file.txt`        | Sort by second column          |
| `sort -k3 -n file.txt`     | Numeric sort by third column   |
| `sort -t ',' -k2 file.csv` | CSV sort using comma delimiter |
| `sort -M file.txt`         | Sort month names               |
| `sort -h file.txt`         | Human-readable sizes           |
| `sort -o out.txt file.txt` | Save output to file            |

---

# Examples

## Example 1: Alphabetical Sort

File:

```text
Banana
Apple
Orange
Mango
```

Command:

```bash
sort fruits.txt
```

Output:

```text
Apple
Banana
Mango
Orange
```

---

## Example 2: Reverse Sort

```bash
sort -r fruits.txt
```

Output:

```text
Orange
Mango
Banana
Apple
```

---

## Example 3: Numeric Sort

File:

```text
100
50
500
25
```

Command:

```bash
sort -n numbers.txt
```

Output:

```text
25
50
100
500
```

Without `-n`:

```bash
sort numbers.txt
```

Output:

```text
100
25
50
500
```

Because default sorting is alphabetical.

---

## Example 4: Remove Duplicates

File:

```text
Apple
Banana
Apple
Orange
Banana
```

Command:

```bash
sort -u fruits.txt
```

Output:

```text
Apple
Banana
Orange
```

---

# Sorting by Columns

File:

```text
John 5000
Alice 7000
Bob 6000
```

---

## Example 5: Sort by Name

```bash
sort -k1 employees.txt
```

Output:

```text
Alice 7000
Bob 6000
John 5000
```

---

## Example 6: Sort by Salary

```bash
sort -k2 -n employees.txt
```

Output:

```text
John 5000
Bob 6000
Alice 7000
```

---

# CSV Sorting

File:

```csv
1,John,50000
2,Alice,70000
3,Bob,60000
```

---

## Example 7: Sort by Name

```bash
sort -t ',' -k2 employees.csv
```

Output:

```text
2,Alice,70000
3,Bob,60000
1,John,50000
```

---

## Example 8: Sort by Salary

```bash
sort -t ',' -k3 -n employees.csv
```

Output:

```text
1,John,50000
3,Bob,60000
2,Alice,70000
```

---

# Human Readable Size Sorting

File:

```text
1K
20M
500K
2G
```

Command:

```bash
sort -h sizes.txt
```

Output:

```text
1K
500K
20M
2G
```

Useful when working with disk usage reports.

---

# Month Sorting

File:

```text
Mar
Jan
Dec
Aug
```

Command:

```bash
sort -M months.txt
```

Output:

```text
Jan
Mar
Aug
Dec
```

---

# Working with Logs

## Example 9: Sort Error Messages

```bash
sort errors.log
```

---

## Example 10: Find Most Common Errors

```bash
sort app.log | uniq -c | sort -nr
```

Output:

```text
150 ERROR
80 WARN
20 INFO
```

Very common interview and DevOps example.

---

# sort with Pipes

## Example 11: Sort Process List

```bash
ps aux | sort
```

---

## Example 12: Sort Usernames

```bash
cut -d: -f1 /etc/passwd | sort
```

---

## Example 13: Sort Open Ports

```bash
netstat -tulpn | sort
```

---

## Example 14: Sort Directory Listing

```bash
ls | sort
```

---

# Save Sorted Output

```bash
sort names.txt > sorted_names.txt
```

Or:

```bash
sort -o sorted_names.txt names.txt
```

---

# sort vs uniq

| Command | Purpose           |
| ------- | ----------------- |
| sort    | Arrange lines     |
| uniq    | Remove duplicates |

Example:

```bash
sort names.txt
uniq names.txt
```

Common combination:

```bash
sort names.txt | uniq
```

---

# sort vs grep

| Command | Purpose      |
| ------- | ------------ |
| grep    | Search text  |
| sort    | Arrange text |

Example:

```bash
grep ERROR app.log | sort
```

---

# Common Interview Questions

### Q1. What does sort do?

Sorts lines of text alphabetically or numerically.

---

### Q2. How do you sort numbers correctly?

```bash
sort -n numbers.txt
```

---

### Q3. How do you remove duplicates?

```bash
sort -u file.txt
```

---

### Q4. How do you sort by second column?

```bash
sort -k2 file.txt
```

---

### Q5. How do you sort CSV files?

```bash
sort -t ',' -k2 file.csv
```

---

# Real-World Examples

### Sort Employee Names

```bash
sort employees.txt
```

---

### Sort Salaries

```bash
sort -k2 -n employees.txt
```

---

### Sort Disk Usage

```bash
du -sh * | sort -h
```

---

### Sort User Accounts

```bash
cut -d: -f1 /etc/passwd | sort
```

---

### Sort and Count Errors

```bash
grep ERROR app.log | sort | uniq -c
```

---

# Related Commands

* uniq
* grep
* awk
* sed
* cut
* wc

---

# Notes

* `sort` is frequently used with `uniq`.
* Use `-n` for numbers.
* Use `-h` for file sizes.
* Use `-t` for CSV files.
* Essential for Linux administration and log analysis.

---

# References

```bash
man sort
info sort
```

---

# Quick Cheat Sheet

```bash
sort file.txt
sort -r file.txt
sort -n file.txt
sort -u file.txt

sort -k2 file.txt
sort -k3 -n file.txt

sort -t ',' -k2 file.csv
sort -t ',' -k3 -n file.csv

sort -h sizes.txt
sort -M months.txt

sort app.log | uniq -c
sort app.log | uniq -c | sort -nr
```
