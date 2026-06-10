# clear — Clear Terminal Screen

## Purpose

The `clear` command is used to clear the contents displayed on the terminal screen.

It does **not delete commands, files, or history**.

It simply removes the visible output from the current terminal window and places the cursor at the top of a clean screen.

This makes the terminal easier to read when a lot of output has accumulated.

---

## Syntax

```bash
clear
```

---

## Basic Example

```bash
clear
```

Before:

```text
$ ls
file1.txt
file2.txt

$ pwd
/home/aman/projects

$ ps aux
...
```

After:

```text
$
```

The screen becomes clean, but command history still exists.

---

## Common Use Cases

### 1. Clean a Cluttered Terminal

```bash
clear
```

After running many commands, clear the screen for better visibility.

---

### 2. Before Starting New Work

```bash
clear
```

Provides a fresh workspace in the terminal.

---

### 3. During Debugging

```bash
clear
```

Remove old logs and focus on new output.

---

### 4. While Monitoring Systems

```bash
top
```

Exit:

```bash
q
```

Then:

```bash
clear
```

Start with a clean screen again.

---

### 5. Before Running Scripts

```bash
clear
./deploy.sh
```

Makes script output easier to read.

---

## Keyboard Shortcut Alternative

Instead of typing:

```bash
clear
```

Press:

```text
Ctrl + L
```

Result:

```text
Screen cleared
```

This is the fastest method used by most Linux users.

---

## Clear vs Reset

### clear

```bash
clear
```

* Clears visible screen
* Keeps terminal state unchanged
* Faster

---

### reset

```bash
reset
```

* Clears screen
* Resets terminal settings
* Useful when terminal becomes corrupted

Example:

```text
Strange characters displayed
Keyboard behaving incorrectly
```

Use:

```bash
reset
```

---

## Common Interview Questions

### Q1. What does clear do?

It clears the terminal screen.

---

### Q2. Does clear delete command history?

No.

History remains available.

Check history:

```bash
history
```

---

### Q3. What is the shortcut for clear?

```text
Ctrl + L
```

---

### Q4. What is the difference between clear and reset?

| Command | Purpose                           |
| ------- | --------------------------------- |
| clear   | Clears screen only                |
| reset   | Clears screen and resets terminal |

---

### Q5. Can you recover previous commands after clear?

Yes.

Use:

```bash
history
```

or

```text
Arrow Up Key
```

---

## Practical Example

Run:

```bash
ls
pwd
date
```

Output:

```text
Documents
Downloads
Projects

/home/aman

Wed Jun 10 10:30:00 UTC 2026
```

Now:

```bash
clear
```

Screen becomes empty, but:

```bash
history
```

still shows all commands.

---

## Related Commands

* history
* reset
* top
* htop
* screen
* tmux

---

## Notes

* `clear` only affects the current terminal view.
* No files are deleted.
* No history is removed.
* Most Linux users use **Ctrl + L** instead of typing `clear`.
* Useful during development, debugging, and system administration.

---

## References

```bash
man clear
```

---

## Quick Cheat Sheet

```bash
clear
Ctrl + L
history
reset
```
