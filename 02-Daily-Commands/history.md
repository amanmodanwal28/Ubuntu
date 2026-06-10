# history — Command History

## Purpose

The `history` command displays the list of commands previously executed in the terminal.

Linux stores command history in a file (usually `~/.bash_history`) so that users can:

* Reuse old commands
* Avoid typing long commands again
* Debug previous work
* Audit terminal activity

It is one of the most useful productivity commands in Linux.

---

## Syntax

```bash
history
```

---

## Basic Example

```bash
history
```

Output:

```text
1  pwd
2  ls -la
3  cd Documents
4  mkdir project
5  touch README.md
6  history
```

The left number is the command number.

---

## Common Options

| Command        | Description                           |                                |
| -------------- | ------------------------------------- | ------------------------------ |
| `history`      | Show complete command history         |                                |
| `history 10`   | Show last 10 commands                 |                                |
| `history       | grep ssh`                             | Search commands containing ssh |
| `history -c`   | Clear current history                 |                                |
| `history -d N` | Delete command number N               |                                |
| `!!`           | Run previous command again            |                                |
| `!N`           | Run command number N                  |                                |
| `!string`      | Run last command starting with string |                                |

---

## Examples

### Example 1: Display Command History

```bash
history
```

Output:

```text
1  pwd
2  ls
3  mkdir project
4  cd project
```

Shows all previously executed commands.

---

### Example 2: Show Last 10 Commands

```bash
history 10
```

Output:

```text
45  ls
46  pwd
47  cd project
48  touch app.py
49  nano app.py
```

Useful when history is very long.

---

### Example 3: Search History

```bash
history | grep ssh
```

Output:

```text
125 ssh root@192.168.0.8
130 ssh user@server
```

Find previously executed SSH commands.

---

### Example 4: Re-run Previous Command

```bash
!!
```

Example:

```bash
pwd
```

Then:

```bash
!!
```

Runs:

```bash
pwd
```

again.

---

### Example 5: Run Specific Command

```bash
!25
```

Executes command number 25 from history.

---

### Example 6: Run Command by Prefix

```bash
!ssh
```

Runs the most recent command starting with:

```text
ssh
```

---

## Common Use Cases

### 1. Find Previously Executed Commands

```bash
history
```

Useful when you forget a command.

---

### 2. Re-run Long Commands

```bash
!!
```

Avoids typing again.

---

### 3. Find SSH Connections

```bash
history | grep ssh
```

Useful for server administrators.

---

### 4. Find Git Commands

```bash
history | grep git
```

Shows recent Git activity.

---

### 5. Audit User Activity

```bash
history
```

Helps understand what commands were executed.

---

### 6. Find Package Installation Commands

```bash
history | grep apt
```

Useful for troubleshooting.

---

### 7. Recover Lost Commands

```bash
history
```

Useful after accidentally clearing the screen.

---

### 8. Repeat Previous sudo Command

```bash
sudo !!
```

Example:

```bash
apt update
```

Permission denied?

Run:

```bash
sudo !!
```

Automatically becomes:

```bash
sudo apt update
```

Very useful trick.

---

## History File Location

Bash stores history in:

```bash
~/.bash_history
```

View it:

```bash
cat ~/.bash_history
```

---

## Clear History

### Clear Current Session

```bash
history -c
```

Removes commands from current shell history.

---

### Clear History File

```bash
history -c
history -w
```

Writes the cleared history to disk.

---

## Keyboard Shortcuts

### Previous Command

```text
↑ (Up Arrow)
```

Show previous command.

---

### Next Command

```text
↓ (Down Arrow)
```

Show next command.

---

### Reverse Search

Press:

```text
Ctrl + R
```

Example:

```text
(reverse-i-search)`ssh':
```

Type part of a command and Bash searches history.

One of the most useful Linux shortcuts.

---

## Common Interview Questions

### Q1. What does history do?

Displays previously executed commands.

---

### Q2. Where is Bash history stored?

```bash
~/.bash_history
```

---

### Q3. How do you search command history?

```bash
history | grep keyword
```

Example:

```bash
history | grep git
```

---

### Q4. What does `!!` do?

Runs the previous command again.

---

### Q5. What is Ctrl + R used for?

Search command history interactively.

---

## Practical Examples

### Find Previous Docker Commands

```bash
history | grep docker
```

---

### Find Previous Python Commands

```bash
history | grep python
```

---

### Find Previous Git Commands

```bash
history | grep git
```

---

### Execute Command Number 50

```bash
!50
```

---

### Execute Last SSH Command

```bash
!ssh
```

---

## Related Commands

* clear
* grep
* cat
* bash
* fc
* alias

---

## Notes

* History is stored per user.
* History survives terminal restarts.
* Use `Ctrl + R` frequently to improve productivity.
* `sudo !!` is one of the most useful Linux shortcuts.
* History helps in debugging, auditing, and automation.

---

## References

```bash
man history
help history
```

---

## Quick Cheat Sheet

```bash
history
history 10
history | grep ssh
history | grep git
!!
!25
!ssh
history -c
history -w
cat ~/.bash_history
Ctrl + R
Up Arrow
Down Arrow
```
