# tee — Read from Standard Input and Write to File

## Purpose

`tee` reads data from standard input (stdin) and writes it to:

1. The terminal (stdout)
2. One or more files simultaneously

Think of `tee` as a **T-junction for data streams**.

It is commonly used for:

* Logging command output
* Saving command results
* Debugging shell scripts
* Monitoring long-running processes
* Creating reports

---

# Syntax

```bash
command | tee [options] file
```

Example:

```bash
ls -l | tee output.txt
```

Output:

```text
(displayed on screen)

AND

saved to output.txt
```

---

# Why Use tee?

Without `tee`:

```bash
ls -l > output.txt
```

Output is saved to file but NOT shown on screen.

With `tee`:

```bash
ls -l | tee output.txt
```

Output is:

* Displayed on screen
* Saved to file

at the same time.

---

# Common Options

| Option            | Description                     |
| ----------------- | ------------------------------- |
| `tee file.txt`    | Write output to file            |
| `tee -a file.txt` | Append instead of overwrite     |
| `tee file1 file2` | Write to multiple files         |
| `tee /dev/null`   | Discard output after displaying |
| `tee -i file.txt` | Ignore interrupt signals        |

---

# Examples

## Example 1: Save Command Output

```bash
ls -l | tee files.txt
```

Output:

```text
Displayed on screen

AND

Saved to files.txt
```

---

## Example 2: Save Disk Usage Report

```bash
df -h | tee disk_report.txt
```

Useful for system audits.

---

## Example 3: Save Memory Information

```bash
free -h | tee memory_report.txt
```

Output appears on screen and is stored.

---

# Append to Existing File

## Example 4

```bash
date | tee -a logfile.txt
```

Output:

```text
Wed Jun 10 10:30:00 IST 2026
```

Appended to existing log file.

---

## Example 5

```bash
echo "Backup Completed" | tee -a backup.log
```

Adds new entry without deleting previous content.

---

# Write to Multiple Files

## Example 6

```bash
echo "Linux" | tee file1.txt file2.txt
```

Result:

```text
file1.txt
file2.txt
```

Both contain:

```text
Linux
```

---

## Example 7

```bash
date | tee report1.txt report2.txt report3.txt
```

Writes to all three files.

---

# Logging Command Output

## Example 8

```bash
ping google.com | tee ping.log
```

Output:

```text
Shown on screen

AND

Saved to ping.log
```

Useful during troubleshooting.

---

## Example 9

```bash
dmesg | tee kernel.log
```

Save kernel messages.

---

## Example 10

```bash
journalctl -xe | tee system_errors.log
```

Save system diagnostics.

---

# Using tee with sudo

Suppose:

```bash
echo "127.0.0.1 myserver" > /etc/hosts
```

Fails because of permissions.

Correct:

```bash
echo "127.0.0.1 myserver" | sudo tee -a /etc/hosts
```

Very common Linux administration trick.

---

# Create Files Quickly

## Example 11

```bash
echo "Hello Linux" | tee hello.txt
```

Creates:

```text
hello.txt
```

Containing:

```text
Hello Linux
```

---

## Example 12

```bash
cat > file.txt
```

Alternative:

```bash
echo "Content" | tee file.txt
```

---

# tee with Pipes

## Example 13

```bash
ps aux | tee processes.txt | grep firefox
```

Explanation:

1. Save full process list
2. Search firefox processes

Simultaneously

---

## Example 14

```bash
df -h | tee disk.txt | grep '/dev'
```

Save full output and filter it.

---

## Example 15

```bash
ip addr | tee network.txt
```

Save network configuration.

---

# Real-Time Monitoring

## Example 16

```bash
tail -f app.log | tee live_output.log
```

Shows logs live and saves them.

---

## Example 17

```bash
ping 8.8.8.8 | tee network_test.log
```

Monitor and save network tests.

---

# Development Examples

## Example 18: Save Build Output

```bash
make | tee build.log
```

Useful when compiling software.

---

## Example 19: Save Python Program Output

```bash
python3 app.py | tee app_output.log
```

---

## Example 20: Save Docker Logs

```bash
docker logs container_name | tee docker.log
```

---

# Embedded Linux Examples

## Save Boot Logs

```bash
dmesg | tee boot.log
```

---

## Save Serial Output

```bash
cat /dev/ttyUSB0 | tee serial.log
```

Useful for board debugging.

---

## Save Network Diagnostics

```bash
ifconfig | tee network_report.txt
```

---

# Linux Administration Examples

### User Report

```bash
cat /etc/passwd | tee users.txt
```

---

### Process Report

```bash
ps aux | tee process_report.txt
```

---

### Package Report

```bash
dpkg -l | tee packages.txt
```

---

### System Information

```bash
uname -a | tee system_info.txt
```

---

# tee vs Redirect Operators

| Method   | Screen Output | Save File |
| -------- | ------------- | --------- |
| `>`      | ❌             | ✅         |
| `>>`     | ❌             | ✅         |
| `tee`    | ✅             | ✅         |
| `tee -a` | ✅             | Append    |

Example:

```bash
ls > output.txt
```

No screen output.

```bash
ls | tee output.txt
```

Screen + File.

---

# Common Interview Questions

### Q1. What does tee do?

Displays output and writes it to file simultaneously.

---

### Q2. How do you append instead of overwrite?

```bash
tee -a file.txt
```

---

### Q3. How do you write to multiple files?

```bash
tee file1.txt file2.txt
```

---

### Q4. Why use tee with sudo?

Because shell redirection (`>`) happens before sudo.

Example:

```bash
echo "data" | sudo tee /etc/file
```

---

### Q5. Difference between `>` and `tee`?

`>` writes only to file.

`tee` writes to file and terminal.

---

# Related Commands

* cat
* echo
* tail
* grep
* awk
* sed
* xargs

---

# Notes

* One of the most useful commands for logging.
* Commonly used in DevOps and Linux Administration.
* Frequently combined with `sudo`.
* Excellent for troubleshooting and report generation.

---

# References

```bash
man tee
info tee
```

---

# Quick Cheat Sheet

```bash
ls -l | tee output.txt

df -h | tee disk.txt

free -h | tee memory.txt

date | tee -a logfile.txt

echo "Hello" | tee file.txt

echo "Entry" | tee -a file.txt

ping google.com | tee ping.log

tail -f app.log | tee live.log

ps aux | tee processes.txt

echo "127.0.0.1 myserver" | sudo tee -a /etc/hosts
```
