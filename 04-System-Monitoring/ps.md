# ps — Process Status

## Purpose

`ps` (Process Status) displays information about currently running processes on a Linux system.

It is one of the most important Linux administration commands used for:

* Monitoring running processes
* Finding Process IDs (PID)
* Checking CPU and Memory usage
* Troubleshooting applications
* Managing services
* Process auditing

Unlike `top`, `ps` shows a **snapshot** of processes at the moment the command is executed.

---

# Syntax

```bash
ps [options]
```

Example:

```bash
ps aux
```

---

# Understanding Process Information

Typical Output:

```text
USER       PID %CPU %MEM COMMAND
root         1  0.0  0.2 systemd
aman      2450  1.5  2.1 firefox
```

Meaning:

| Column  | Description             |
| ------- | ----------------------- |
| USER    | Process owner           |
| PID     | Process ID              |
| %CPU    | CPU usage percentage    |
| %MEM    | Memory usage percentage |
| COMMAND | Executed command        |

---

# Common Commands

| Command                        | Description                      |
| ------------------------------ | -------------------------------- |
| `ps`                           | Current shell processes          |
| `ps aux`                       | All running processes            |
| `ps -ef`                       | Full-format process list         |
| `ps -u username`               | Processes of a specific user     |
| `ps -p PID`                    | Information about a specific PID |
| `ps --sort=-%cpu`              | Sort by CPU usage                |
| `ps --sort=-%mem`              | Sort by Memory usage             |
| `ps -o pid,user,%cpu,%mem,cmd` | Custom output columns            |
| `ps -ef --forest`              | Process tree view                |
| `ps auxww`                     | Full command line output         |

---

# Examples

## Example 1: Show Current Shell Processes

```bash
ps
```

Output:

```text
PID TTY          TIME CMD
1456 pts/0   00:00:00 bash
1521 pts/0   00:00:00 ps
```

Shows processes running in the current terminal session.

---

## Example 2: Show All Processes

```bash
ps aux
```

Output:

```text
USER       PID %CPU %MEM COMMAND
root         1  0.0  0.1 systemd
root       534  0.0  0.2 sshd
aman      2450  1.5  2.1 firefox
```

Most commonly used form.

---

## Example 3: Full Format Listing

```bash
ps -ef
```

Output:

```text
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Jun10 ?        00:00:02 systemd
```

Useful for troubleshooting services.

---

## Example 4: Specific User Processes

```bash
ps -u aman
```

Output:

```text
PID TTY          TIME CMD
2450 pts/0   00:00:01 firefox
```

Shows only the selected user's processes.

---

## Example 5: Specific PID Information

```bash
ps -p 2450
```

Output:

```text
PID TTY          TIME CMD
2450 pts/0   00:00:01 firefox
```

Useful when you already know the PID.

---

# Finding Processes

## Example 6: Find Nginx Process

```bash
ps aux | grep nginx
```

Output:

```text
root      1100  0.0  0.3 nginx
www-data  1101  0.0  0.2 nginx
```

Very common Linux administration task.

---

## Example 7: Find Python Processes

```bash
ps aux | grep python
```

Useful when debugging Python applications.

---

## Example 8: Find SSH Processes

```bash
ps aux | grep ssh
```

Shows SSH sessions and services.

---

# CPU Usage Analysis

## Example 9: Top CPU Consumers

```bash
ps aux --sort=-%cpu | head -10
```

Output:

```text
USER PID %CPU COMMAND
aman 2450 45.2 firefox
```

Useful when the system feels slow.

---

## Example 10: Top 5 CPU Processes

```bash
ps aux --sort=-%cpu | head -5
```

Quick performance check.

---

# Memory Usage Analysis

## Example 11: Top Memory Consumers

```bash
ps aux --sort=-%mem | head -10
```

Output:

```text
USER PID %MEM COMMAND
aman 2450 15.1 firefox
```

Useful for RAM troubleshooting.

---

## Example 12: Top 5 Memory Processes

```bash
ps aux --sort=-%mem | head -5
```

Helps identify memory leaks.

---

# Custom Output

## Example 13

```bash
ps -o pid,user,%cpu,%mem,cmd
```

Output:

```text
PID USER %CPU %MEM CMD
2450 aman 1.5 2.1 firefox
```

Displays only selected columns.

---

## Example 14

```bash
ps -p 2450 -o pid,ppid,%cpu,%mem,cmd
```

Output:

```text
PID PPID %CPU %MEM CMD
2450 1200 1.5 2.1 firefox
```

Useful for debugging specific processes.

---

# Process Tree

## Example 15

```bash
ps -ef --forest
```

Output:

```text
root
 ├─systemd
 │  ├─sshd
 │  └─cron
```

Shows parent-child relationships.

---

## Example 16

```bash
ps axjf
```

Another process tree view.

---

# Zombie Process Detection

## Example 17

```bash
ps aux | grep Z
```

Output:

```text
USER PID STAT COMMAND
root 2500 Z zombie_process
```

Zombie processes consume process table entries.

---

# Service Troubleshooting

## Example 18: Check Apache

```bash
ps aux | grep apache2
```

---

## Example 19: Check Docker

```bash
ps aux | grep docker
```

---

## Example 20: Check PostgreSQL

```bash
ps aux | grep postgres
```

---

# Real-World Examples

### Find Running Python Scripts

```bash
ps aux | grep python
```

---

### Check if SSH Server is Running

```bash
ps aux | grep sshd
```

---

### Find Java Applications

```bash
ps aux | grep java
```

---

### Monitor Embedded Linux Application

```bash
ps aux | grep my_app
```

---

### Find Application PID Before Killing

```bash
ps aux | grep firefox
```

Then:

```bash
kill PID
```

---

# ps vs top

| Command | Behavior             |
| ------- | -------------------- |
| `ps`    | Snapshot             |
| `top`   | Real-time monitoring |

Example:

```bash
ps aux
top
```

---

# ps vs pgrep

| Command | Purpose                      |
| ------- | ---------------------------- |
| ps      | Detailed process information |
| pgrep   | Return PID only              |

Example:

```bash
ps aux | grep nginx

pgrep nginx
```

---

# Common Interview Questions

### Q1. What does ps do?

Displays information about running processes.

---

### Q2. What is PID?

Process Identifier.

Every running process has a unique PID.

---

### Q3. How do you find a process by name?

```bash
ps aux | grep process_name
```

---

### Q4. How do you show top CPU-consuming processes?

```bash
ps aux --sort=-%cpu | head
```

---

### Q5. How do you show top memory-consuming processes?

```bash
ps aux --sort=-%mem | head
```

---

# Related Commands

* top
* htop
* pgrep
* pidof
* kill
* killall
* nice
* renice

---

# Notes

* `ps aux` is one of the most frequently used Linux commands.
* Use `ps -ef --forest` for process hierarchy.
* Use sorting options for CPU and memory troubleshooting.
* Often combined with `grep` for process searching.

---

# References

```bash
man ps
info ps
```

---

# Quick Cheat Sheet

```bash
ps

ps aux

ps -ef

ps -u username

ps -p PID

ps aux | grep nginx

ps aux | grep python

ps aux --sort=-%cpu | head

ps aux --sort=-%mem | head

ps -ef --forest

ps -o pid,user,%cpu,%mem,cmd

ps -p PID -o pid,ppid,%cpu,%mem,cmd
```
