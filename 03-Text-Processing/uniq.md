# uniq — Remove or Report Duplicate Lines

## Purpose

`uniq` filters out repeated lines from sorted input. It is commonly used to remove duplicates, count occurrences, and generate frequency reports.

⚠️ Important: `uniq` only works on **adjacent duplicate lines**. Therefore, it is usually used together with `sort`.

---

## Syntax

```bash
uniq [options] file
```

Example:

```bash
uniq names.txt
```

---

# Understanding uniq

File:

```text
Apple
Apple
Banana
Banana
Banana
Orange
```

Command:

```bash
uniq fruits.txt
```

Output:

```text
Apple
Banana
Orange
```

---

# Why sort is Often Required

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
uniq fruits.txt
```

Output:

```text
Apple
Banana
Apple
Orange
Banana
```

Nothing changes because duplicates are not adjacent.

Correct way:

```bash
sort fruits.txt | uniq
```

Output:

```text
Apple
Banana
Orange
```

---

# Common Commands

| Command                 | Description                |
| ----------------------- | -------------------------- |
| `uniq file.txt`         | Remove adjacent duplicates |
| `sort file.txt \| uniq` | Remove all duplicates      |
| `uniq -c file.txt`      | Count occurrences          |
| `uniq -d file.txt`      | Show duplicate lines only  |
| `uniq -u file.txt`      | Show unique lines only     |
| `uniq -i file.txt`      | Ignore case                |
| `uniq -f 1 file.txt`    | Skip first field           |
| `uniq -s 3 file.txt`    | Skip first 3 characters    |

---

# Examples

## Example 1: Remove Duplicate Lines

File:

```text
Apple
Apple
Banana
Banana
Orange
```

Command:

```bash
uniq fruits.txt
```

Output:

```text
Apple
Banana
Orange
```

---

## Example 2: Count Occurrences

```bash
uniq -c fruits.txt
```

Output:

```text
      2 Apple
      2 Banana
      1 Orange
```

---

## Example 3: Show Duplicates Only

```bash
uniq -d fruits.txt
```

Output:

```text
Apple
Banana
```

---

## Example 4: Show Unique Lines Only

```bash
uniq -u fruits.txt
```

Output:

```text
Orange
```

---

## Example 5: Ignore Case

File:

```text
apple
Apple
APPLE
banana
```

Command:

```bash
uniq -i fruits.txt
```

Better:

```bash
sort -f fruits.txt | uniq -i
```

Output:

```text
apple
banana
```

---

# Counting Most Frequent Values

File:

```text
ERROR
ERROR
WARN
INFO
ERROR
WARN
```

Command:

```bash
sort logs.txt | uniq -c
```

Output:

```text
3 ERROR
1 INFO
2 WARN
```

---

## Example 6: Sort by Frequency

```bash
sort logs.txt | uniq -c | sort -nr
```

Output:

```text
3 ERROR
2 WARN
1 INFO
```

Very common DevOps and Linux administration command.

---

# Working with Files

## Example 7: Unique Usernames

```bash
cut -d: -f1 /etc/passwd | sort | uniq
```

---

## Example 8: Count Usernames

```bash
cut -d: -f1 /etc/passwd | sort | uniq -c
```

---

## Example 9: Remove Duplicate IP Addresses

```bash
sort access.log | uniq
```

---

# Working with Logs

## Example 10: Count Error Types

```bash
grep ERROR app.log | sort | uniq -c
```

---

## Example 11: Most Common Messages

```bash
cat app.log | sort | uniq -c | sort -nr
```

Output:

```text
150 ERROR Database Failed
80 WARN Disk Space Low
20 INFO Started
```

---

# uniq with Pipes

## Find Unique Processes

```bash
ps aux | awk '{print $11}' | sort | uniq
```

---

## Count Running Commands

```bash
ps aux | awk '{print $11}' | sort | uniq -c
```

---

## Unique Open Ports

```bash
netstat -tulpn | awk '{print $4}' | sort | uniq
```

---

# Real-World Examples

### Count HTTP Status Codes

```bash
awk '{print $9}' access.log | sort | uniq -c
```

Output:

```text
500 404
250 200
10 500
```

---

### Most Common IP Addresses

```bash
awk '{print $1}' access.log | sort | uniq -c | sort -nr
```

---

### Count Login Attempts

```bash
grep "Failed password" auth.log | sort | uniq -c
```

---

### Find Duplicate Files List

```bash
find . -type f | sort | uniq -d
```

---

# uniq vs sort

| Command | Purpose                 |
| ------- | ----------------------- |
| `sort`  | Arrange lines           |
| `uniq`  | Remove/count duplicates |

Example:

```bash
sort names.txt
sort names.txt | uniq
```

---

# uniq vs wc

| Command   | Purpose                 |
| --------- | ----------------------- |
| `uniq -c` | Count each unique value |
| `wc -l`   | Count total lines       |

Example:

```bash
sort file.txt | uniq -c
wc -l file.txt
```

---

# Common Interview Questions

### Q1. What does uniq do?

Removes or reports duplicate adjacent lines.

---

### Q2. Why is sort often used before uniq?

Because `uniq` only removes adjacent duplicates.

---

### Q3. How do you count duplicates?

```bash
uniq -c file.txt
```

---

### Q4. How do you show only duplicate lines?

```bash
uniq -d file.txt
```

---

### Q5. How do you show only unique lines?

```bash
uniq -u file.txt
```

---

# Related Commands

* sort
* grep
* awk
* sed
* cut
* wc

---

# Notes

* `uniq` works only on adjacent duplicates.
* Use `sort | uniq` for reliable duplicate removal.
* Very common in log analysis and reporting.
* Frequently combined with `awk`, `grep`, and `sort`.

---

# References

```bash
man uniq
info uniq
```

---

# Quick Cheat Sheet

```bash
uniq file.txt

sort file.txt | uniq

uniq -c file.txt

uniq -d file.txt

uniq -u file.txt

sort app.log | uniq -c

sort app.log | uniq -c | sort -nr

awk '{print $1}' access.log | sort | uniq -c

cut -d: -f1 /etc/passwd | sort | uniq
```
