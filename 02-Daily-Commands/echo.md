# echo — Display Text and Variables

## Purpose

The `echo` command is used to display text, variables, and values in the terminal.

It is one of the most commonly used Linux commands and is heavily used in:

* Shell scripting
* Debugging
* Logging
* File creation
* Environment variable inspection

Think of `echo` as the Linux equivalent of **print()** in programming languages.

---

## Syntax

```bash
echo [options] "text"
```

---

## Basic Examples

### Print Text

```bash
echo "Hello World"
```

Output:

```text
Hello World
```

---

### Print Multiple Words

```bash
echo Linux is awesome
```

Output:

```text
Linux is awesome
```

---

### Print Numbers

```bash
echo 100
```

Output:

```text
100
```

---

## Common Options

| Command                   | Description              |
| ------------------------- | ------------------------ |
| `echo "text"`             | Display text             |
| `echo $VAR`               | Display variable value   |
| `echo -n "text"`          | Print without newline    |
| `echo -e "text"`          | Enable escape characters |
| `echo "text" > file.txt`  | Write text to file       |
| `echo "text" >> file.txt` | Append text to file      |

---

## Examples

### Example 1: Display Current User

```bash
echo $USER
```

Output:

```text
aman
```

Displays the logged-in user.

---

### Example 2: Display Home Directory

```bash
echo $HOME
```

Output:

```text
/home/aman
```

Shows the user's home directory.

---

### Example 3: Print Current Shell

```bash
echo $SHELL
```

Output:

```text
/bin/bash
```

Shows the active shell.

---

### Example 4: Print Multiple Lines

```bash
echo -e "Line 1\nLine 2\nLine 3"
```

Output:

```text
Line 1
Line 2
Line 3
```

---

### Example 5: Use Tab Character

```bash
echo -e "Name\tAge"
```

Output:

```text
Name    Age
```

---

## Common Escape Characters

| Character | Meaning         |
| --------- | --------------- |
| `\n`      | New Line        |
| `\t`      | Tab             |
| `\\`      | Backslash       |
| `\"`      | Double Quote    |
| `\a`      | Alert/Bell      |
| `\r`      | Carriage Return |

Example:

```bash
echo -e "Linux\nUbuntu\nDebian"
```

Output:

```text
Linux
Ubuntu
Debian
```

---

## Writing Data to Files

### Create a File

```bash
echo "Hello Linux" > file.txt
```

Content:

```text
Hello Linux
```

---

### Append Data

```bash
echo "Second Line" >> file.txt
```

Content:

```text
Hello Linux
Second Line
```

---

### Overwrite Existing File

```bash
echo "New Content" > file.txt
```

Previous content is replaced.

---

## Common Use Cases

### 1. Display Messages

```bash
echo "Backup Started"
```

Used in scripts.

---

### 2. Print Variables

```bash
echo $PATH
```

Shows system PATH.

---

### 3. Create README File

```bash
echo "# My Project" > README.md
```

Creates a Markdown file.

---

### 4. Log Script Status

```bash
echo "Deployment Completed"
```

Useful in automation scripts.

---

### 5. Create Configuration Files

```bash
echo "PORT=8080" > .env
```

Creates environment variable files.

---

### 6. Test Variable Values

```bash
NAME="Aman"

echo $NAME
```

Output:

```text
Aman
```

---

### 7. Display Current Directory

```bash
echo $PWD
```

Output:

```text
/home/aman/project
```

---

### 8. Generate Simple Reports

```bash
echo "Disk Usage Report"
```

Used in shell scripts.

---

## Redirecting Output

### Standard Output

```bash
echo "Hello"
```

Output:

```text
Hello
```

---

### Redirect to File

```bash
echo "Hello" > output.txt
```

Writes to file.

---

### Append to File

```bash
echo "World" >> output.txt
```

Adds content at the end.

---

## Practical Examples

### Create a Python File

```bash
echo 'print("Hello World")' > hello.py
```

Run:

```bash
python3 hello.py
```

Output:

```text
Hello World
```

---

### Create Multiple Files

```bash
echo "# Project" > README.md

echo "print('Hello')" > main.py
```

---

### Check Environment Variable

```bash
echo $PATH
```

Displays executable search paths.

---

### Save Current Date

```bash
echo $(date)
```

Output:

```text
Wed Jun 10 10:30:00 UTC 2026
```

---

## Common Interview Questions

### Q1. What does echo do?

Displays text, variables, and values.

---

### Q2. What is the difference between `>` and `>>`?

| Operator | Meaning        |
| -------- | -------------- |
| `>`      | Overwrite file |
| `>>`     | Append to file |

---

### Q3. How do you print a variable?

```bash
echo $USER
```

---

### Q4. What does `-e` do?

Enables escape characters.

Example:

```bash
echo -e "A\nB"
```

Output:

```text
A
B
```

---

### Q5. How do you print without a newline?

```bash
echo -n "Hello"
```

---

## Difference Between echo and printf

| Feature             | echo    | printf   |
| ------------------- | ------- | -------- |
| Simple output       | Yes     | Yes      |
| Formatting          | Limited | Advanced |
| Common in scripts   | Yes     | Yes      |
| Similar to C printf | No      | Yes      |

Example:

```bash
printf "Name: %s\n" "Aman"
```

Output:

```text
Name: Aman
```

---

## Related Commands

* printf
* cat
* touch
* tee
* env
* export

---

## Notes

* `echo` is one of the most frequently used Linux commands.
* Useful for displaying variables and debugging scripts.
* Commonly used with output redirection (`>` and `>>`).
* Often considered the Linux version of `print()`.

---

## References

```bash
man echo
help echo
```

---

## Quick Cheat Sheet

```bash
echo "Hello World"
echo $USER
echo $HOME
echo $PATH
echo -n "Hello"
echo -e "A\nB\nC"
echo "Hello" > file.txt
echo "World" >> file.txt
echo $(date)
echo $PWD
```
