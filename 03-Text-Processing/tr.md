# tr — Translate or Delete Characters

## Purpose

`tr` (translate) is used to:

* Replace characters
* Convert lowercase to uppercase
* Convert uppercase to lowercase
* Delete characters
* Remove duplicate characters
* Clean text streams

Unlike `sed`, `tr` works on **characters**, not lines.

It is commonly used in:

* Shell scripting
* Log processing
* Text cleanup
* Data transformation
* Linux automation

---

# Syntax

```bash
tr [OPTION] SET1 [SET2]
```

Example:

```bash
echo "linux" | tr 'a-z' 'A-Z'
```

Output:

```text
LINUX
```

---

# Understanding tr

Input:

```text
linux
```

Command:

```bash
echo "linux" | tr 'a-z' 'A-Z'
```

Output:

```text
LINUX
```

Each character from SET1 is replaced by the corresponding character in SET2.

---

# Common Commands

| Command          | Description              |
| ---------------- | ------------------------ |
| `tr 'a-z' 'A-Z'` | lowercase → uppercase    |
| `tr 'A-Z' 'a-z'` | uppercase → lowercase    |
| `tr -d '0-9'`    | delete digits            |
| `tr -d ' '`      | remove spaces            |
| `tr -s ' '`      | squeeze repeated spaces  |
| `tr -s '\n'`     | squeeze blank lines      |
| `tr ',' ':'`     | replace comma with colon |
| `tr -cd '0-9'`   | keep only digits         |

---

# Examples

## Example 1: Lowercase to Uppercase

```bash
echo "ubuntu linux" | tr 'a-z' 'A-Z'
```

Output:

```text
UBUNTU LINUX
```

---

## Example 2: Uppercase to Lowercase

```bash
echo "LINUX" | tr 'A-Z' 'a-z'
```

Output:

```text
linux
```

---

## Example 3: Replace Characters

```bash
echo "2026/06/10" | tr '/' '-'
```

Output:

```text
2026-06-10
```

---

## Example 4: Replace Comma with Colon

```bash
echo "John,Alice,Bob" | tr ',' ':'
```

Output:

```text
John:Alice:Bob
```

---

# Deleting Characters

## Example 5: Remove Digits

```bash
echo "Linux123Ubuntu456" | tr -d '0-9'
```

Output:

```text
LinuxUbuntu
```

---

## Example 6: Remove Spaces

```bash
echo "Hello Linux World" | tr -d ' '
```

Output:

```text
HelloLinuxWorld
```

---

## Example 7: Remove Special Characters

```bash
echo "abc@#$123" | tr -d '@#$'
```

Output:

```text
abc123
```

---

# Keeping Specific Characters

## Example 8: Keep Only Digits

```bash
echo "Order#12345" | tr -cd '0-9'
```

Output:

```text
12345
```

---

## Example 9: Keep Only Alphabets

```bash
echo "abc123XYZ" | tr -cd 'a-zA-Z'
```

Output:

```text
abcXYZ
```

---

# Squeezing Repeated Characters

## Example 10: Remove Extra Spaces

Input:

```text
Linux     Ubuntu     Debian
```

Command:

```bash
echo "Linux     Ubuntu     Debian" | tr -s ' '
```

Output:

```text
Linux Ubuntu Debian
```

---

## Example 11: Remove Multiple Blank Lines

```bash
cat file.txt | tr -s '\n'
```

Converts multiple blank lines into one.

---

# Working with Files

## Example 12: Convert File to Uppercase

```bash
cat file.txt | tr 'a-z' 'A-Z'
```

---

## Example 13: Convert File to Lowercase

```bash
cat file.txt | tr 'A-Z' 'a-z'
```

---

## Example 14: Remove Numbers from File

```bash
cat file.txt | tr -d '0-9'
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

## Example 15: Change Delimiter

```bash
cat employees.csv | tr ',' ':'
```

Output:

```text
1:John:50000
2:Alice:70000
3:Bob:60000
```

---

# Working with Logs

## Example 16: Convert Logs to Uppercase

```bash
cat app.log | tr 'a-z' 'A-Z'
```

---

## Example 17: Remove Tabs

```bash
cat app.log | tr -d '\t'
```

---

## Example 18: Clean Log Spacing

```bash
cat app.log | tr -s ' '
```

---

# tr with Pipes

## Example 19: Count Unique Words

```bash
cat file.txt | tr ' ' '\n' | sort | uniq
```

Explanation:

* Convert spaces to newlines
* Sort words
* Remove duplicates

---

## Example 20: Extract Numbers

```bash
echo "CPU Usage: 85%" | tr -cd '0-9'
```

Output:

```text
85
```

---

## Example 21: Username Cleanup

```bash
echo "AMAN MODANWAL" | tr 'A-Z' 'a-z'
```

Output:

```text
aman modanwal
```

---

# Real-World Examples

### Remove Windows Carriage Returns

```bash
tr -d '\r' < windows_file.txt
```

---

### Generate Password-Friendly String

```bash
echo "Linux Ubuntu 2026" | tr -d ' '
```

Output:

```text
LinuxUbuntu2026
```

---

### Convert CSV to Colon Format

```bash
cat users.csv | tr ',' ':'
```

---

### Remove Blank Spaces

```bash
cat file.txt | tr -s ' '
```

---

### Extract Numbers from Logs

```bash
grep ERROR app.log | tr -cd '0-9\n'
```

---

# tr vs sed vs awk

| Tool | Purpose               |
| ---- | --------------------- |
| tr   | Character translation |
| sed  | Line editing          |
| awk  | Field processing      |

Example:

```bash
echo "linux" | tr 'a-z' 'A-Z'

sed 's/linux/ubuntu/' file.txt

awk '{print $1}' file.txt
```

---

# Common Interview Questions

### Q1. What is tr used for?

Character translation, deletion, and text cleanup.

---

### Q2. How do you convert lowercase to uppercase?

```bash
tr 'a-z' 'A-Z'
```

---

### Q3. How do you delete digits?

```bash
tr -d '0-9'
```

---

### Q4. What does `-s` do?

Squeezes repeated characters into one.

Example:

```bash
tr -s ' '
```

---

### Q5. How do you keep only digits?

```bash
tr -cd '0-9'
```

---

# Related Commands

* awk
* sed
* grep
* sort
* uniq
* cut
* paste

---

# Notes

* `tr` works on characters, not lines.
* Often used with pipes.
* Useful for text cleaning and formatting.
* Frequently combined with `sort`, `uniq`, and `grep`.

---

# References

```bash
man tr
info tr
```

---

# Quick Cheat Sheet

```bash
tr 'a-z' 'A-Z'

tr 'A-Z' 'a-z'

tr -d '0-9'

tr -d ' '

tr -s ' '

tr ',' ':'

tr -cd '0-9'

tr -cd 'a-zA-Z'

cat file.txt | tr 'a-z' 'A-Z'

cat file.txt | tr -d '\r'
```
