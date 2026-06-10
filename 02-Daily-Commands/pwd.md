# pwd — Print Working Directory

## English Explanation

The `pwd` command stands for **Print Working Directory**.

It displays the absolute path of the current directory you are working in.It helps you identify your exact location in the Linux filesystem at any moment.

This is one of the most basic and commonly used Linux commands, especially when navigating through directories.

---

## Syntax

```bash
pwd [option]
```

---

## Common Flags

| Flag     | Description                                      |
| -------- | ------------------------------------------------ |
| `pwd`    | Display the current directory path               |
| `pwd -L` | Show the logical path (follows symbolic links)   |
| `pwd -P` | Show the physical path (resolves symbolic links) |

---

## Examples

### Example 1: Display Current Directory

```bash
pwd
```

Output:

```text
/home/aman/Documents
```

This command shows the complete path of the current working directory.

---

### Example 2: Show Physical Path

```bash
pwd -P
```

Output:

```text
/home/aman/projects
```

This command displays the real physical directory path after resolving symbolic links.

---

## Common Use Cases

1. Verify your current location after opening a terminal.

```bash
pwd
```

2. Store the current directory path inside a shell script.

```bash
CURRENT_DIR=$(pwd)
echo $CURRENT_DIR
```

3. Determine the base path before using relative paths.

4. Check the real path of a symbolic link.

```bash
pwd -P
```

5. Verify locations when multiple terminal windows are open.

6. Confirm that you successfully changed directories.

```bash
cd /var/log
pwd
```

7. Debug shell scripts by tracking where they are executed.

8. Detect the project root directory dynamically in build scripts or Makefiles.

```bash
PROJECT_ROOT=$(pwd)
```

---

## Difference Between `pwd -L` and `pwd -P`

### Logical Path (`pwd -L`)

Displays the path exactly as you navigated it, including symbolic links.

```bash
pwd -L
```

Example:

```text
/home/aman/link_to_project
```

### Physical Path (`pwd -P`)

Displays the actual filesystem location after resolving symbolic links.

```bash
pwd -P
```

Example:

```text
/home/aman/projects/my_project
```

---

## Why Use `pwd`?

The `pwd` command helps users:

* Know their current location in the filesystem
* Avoid working in the wrong directory
* Build scripts that depend on the current path
* Debug shell scripts and automation tasks
* Work efficiently with relative and absolute paths

It is one of the first commands every Linux user should learn and use regularly.
