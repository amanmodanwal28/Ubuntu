# wc — Count Lines, Words, and Characters

## Purpose

`wc` stands for **Word Count**.

It is used to count:

* Lines
* Words
* Characters
* Bytes

`wc` is commonly used for:

* Log analysis
* File statistics
* Script automation
* Counting command output

It works with both files and command output through pipes.

---

## Syntax

```bash
wc [options] file_name
```

Example:

```bash
wc notes.txt
```

---

## Common Commands

| Command          | Description                  |
| ---------------- | ---------------------------- |
| `wc file.txt`    | Show lines, words, and bytes |
| `wc -l file.txt` | Count lines only             |
| `wc -w file.txt` | Count words only             |
| `wc -c file.txt` | Count bytes                  |
| `wc -m file.txt` | Count characters             |
| `wc -L file.txt` | Length of longest line       |

---

## Examples

### Example 1: Basic Count

Create a file:

```bash
echo "Linux is awesome" > notes.txt
```

Run:

```bash
wc notes.txt
```

Output:

```text
1 3 17 notes.txt
```

Meaning:

| Value | Meaning |
| ----- | ------- |
| 1     | Lines   |
| 3     | Words   |
| 17    | Bytes   |

---

### Example 2: Count Lines

```bash
wc -l notes.txt
```

Output:

```text
1 notes.txt
```

Shows only line count.

---

### Example 3: Count Words

```bash
wc -w notes.txt
```

Output:

```text
3 notes.txt
```

---

### Example 4: Count Bytes

```bash
wc -c notes.txt
```

Output:

```text
17 notes.txt
```

Useful for file size verification.

---

### Example 5: Count Characters

```bash
wc -m notes.txt
```

Output:

```text
16 notes.txt
```

Character count may differ from byte count when using Unicode characters.

---

### Example 6: Longest Line

```bash
wc -L notes.txt
```

Output:

```text
16 notes.txt
```

Shows the length of the longest line.

---

## Common Use Cases

### 1. Count Log Entries

```bash
wc -l app.log
```

Output:

```text
1500 app.log
```

Useful for log analysis.

---

### 2. Count Error Messages

```bash
grep ERROR app.log | wc -l
```

Output:

```text
35
```

Shows total errors.

---

### 3. Count Python Files

```bash
ls *.py | wc -l
```

Output:

```text
12
```

Counts Python files in current directory.

---

### 4. Count CSV Records

```bash
wc -l data.csv
```

Output:

```text
5000 data.csv
```

Useful for datasets.

---

### 5. Verify Empty File

```bash
wc -l empty.txt
```

Output:

```text
0 empty.txt
```

Or:

```bash
[ $(wc -l < empty.txt) -eq 0 ]
```

Used in scripts.

---

### 6. Count Non-Comment Lines

```bash
grep -v '^#' config.conf | wc -l
```

Counts active configuration entries.

---

### 7. Count Unique IP Addresses

```bash
cut -d' ' -f1 access.log | sort -u | wc -l
```

Output:

```text
245
```

Shows unique visitors.

---

### 8. Count Running Processes

```bash
ps aux | wc -l
```

Shows total running processes.

---

### 9. Count Search Results

```bash
find . -name "*.conf" | wc -l
```

Counts configuration files.

---

### 10. Count Files in Directory

```bash
ls | wc -l
```

Displays total files and folders.

---

## Using wc with Pipes

### Count Error Lines

```bash
grep ERROR app.log | wc -l
```

---

### Count Active Services

```bash
systemctl list-units --type=service | wc -l
```

---

### Count Open Ports

```bash
ss -tuln | wc -l
```

---

### Count Logged-In Users

```bash
who | wc -l
```

---

### Count Installed Packages

Ubuntu:

```bash
dpkg -l | wc -l
```

---

## wc vs ls vs grep

| Command | Purpose     |
| ------- | ----------- |
| wc      | Count       |
| ls      | List files  |
| grep    | Search text |

Example:

```bash
ls *.py | wc -l
```

List files and count them.

---

### Search and Count

```bash
grep ERROR app.log | wc -l
```

Search matching lines and count them.

---

## Common Interview Questions

### Q1. What does wc stand for?

Word Count.

---

### Q2. How do you count lines?

```bash
wc -l file.txt
```

---

### Q3. How do you count words?

```bash
wc -w file.txt
```

---

### Q4. How do you count characters?

```bash
wc -m file.txt
```

---

### Q5. How do you count matching grep results?

```bash
grep ERROR app.log | wc -l
```

---

## Practical Examples

### Count Log Entries

```bash
wc -l app.log
```

---

### Count Python Files

```bash
ls *.py | wc -l
```

---

### Count TODO Comments

```bash
grep -r "TODO" . | wc -l
```

---

### Count Configuration Files

```bash
find /etc -name "*.conf" | wc -l
```

---

### Count Unique Users

```bash
cut -d: -f1 /etc/passwd | wc -l
```

---

## Related Commands

* grep
* cat
* sort
* uniq
* cut
* find

---

## Notes

* `wc` is simple but extremely useful.
* Frequently used with pipes (`|`).
* Essential for log analysis and scripting.
* Helps count search results, files, users, and records.
* One of the most commonly used text-processing commands.

---

## References

```bash
man wc
info wc
```

---

## Quick Cheat Sheet

```bash
wc file.txt
wc -l file.txt
wc -w file.txt
wc -c file.txt
wc -m file.txt
wc -L file.txt

grep ERROR app.log | wc -l
ls *.py | wc -l
find . -name "*.conf" | wc -l
who | wc -l
```
