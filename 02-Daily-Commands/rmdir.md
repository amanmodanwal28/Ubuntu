# rmdir — Remove Empty Directories

## Purpose

The `rmdir` command stands for **Remove Directory**.

It is used to delete **empty directories** in Linux.

Unlike `rm -r`, the `rmdir` command can only remove directories that contain no files or subdirectories.

Because it only removes empty directories, it is considered a safer alternative to `rm -r`.

---

## Syntax

```bash
rmdir [options] directory_name
```

---

## Common Options

| Command                            | Description                                   |
| ---------------------------------- | --------------------------------------------- |
| `rmdir directory`                  | Remove an empty directory                     |
| `rmdir dir1 dir2 dir3`             | Remove multiple empty directories             |
| `rmdir -p parent/child/grandchild` | Remove directory and empty parent directories |
| `rmdir -v directory`               | Show detailed output                          |

---

## Examples

### Example 1: Remove an Empty Directory

```bash
rmdir project
```

Before:

```text
project/
```

After:

```text
Directory removed
```

The directory is deleted because it is empty.

---

### Example 2: Remove Multiple Directories

```bash
rmdir test1 test2 test3
```

Before:

```text
test1/
test2/
test3/
```

After:

```text
All directories removed
```

All directories must be empty.

---

### Example 3: Remove Parent Directories

```bash
rmdir -p project/src/python
```

Before:

```text
project/
└── src/
    └── python/
```

After:

```text
All empty directories removed
```

The `-p` option removes:

```text
python/
src/
project/
```

if all are empty.

---

### Example 4: Verbose Mode

```bash
rmdir -v backup
```

Output:

```text
rmdir: removing directory 'backup'
```

Useful in shell scripts.

---

## Common Use Cases

### 1. Remove Empty Test Directories

```bash
rmdir test_folder
```

Used after testing.

---

### 2. Clean Empty Project Folders

```bash
rmdir old_project
```

Removes unused directories.

---

### 3. Remove Nested Empty Directories

```bash
rmdir -p project/src/tmp
```

Deletes all empty parent directories.

---

### 4. Clean Build Structures

```bash
rmdir build/cache
```

Useful after cleanup operations.

---

### 5. Remove Empty Backup Directories

```bash
rmdir backup_old
```

Keeps filesystem organized.

---

## What Happens If Directory Is Not Empty?

Command:

```bash
rmdir project
```

Output:

```text
rmdir: failed to remove 'project': Directory not empty
```

Example:

```text
project/
└── app.py
```

Since the directory contains files, `rmdir` cannot remove it.

---

## Removing Non-Empty Directories

Use:

```bash
rm -r project
```

or

```bash
rm -rf project
```

⚠️ Be careful because these commands permanently delete files.

---

## Difference Between rmdir and rm -r

| Feature                       | rmdir | rm -r |
| ----------------------------- | ----- | ----- |
| Removes empty directories     | Yes   | Yes   |
| Removes non-empty directories | No    | Yes   |
| Removes files                 | No    | Yes   |
| Safer to use                  | Yes   | No    |
| Recursive deletion            | No    | Yes   |

Example:

```bash
rmdir test
```

Only works if `test` is empty.

---

## Common Interview Questions

### Q1. What does rmdir stand for?

Remove Directory.

---

### Q2. Can rmdir delete files?

No.

It only removes empty directories.

---

### Q3. What happens if the directory is not empty?

```bash
rmdir project
```

Output:

```text
Directory not empty
```

The command fails.

---

### Q4. What does the `-p` option do?

```bash
rmdir -p project/src/python
```

Removes:

* python
* src
* project

if all are empty.

---

### Q5. When should you use rmdir instead of rm -r?

Use `rmdir` when:

* You only want to remove empty directories.
* You want a safer deletion method.
* You want to avoid accidentally deleting files.

---

## Related Commands

* rm
* mkdir
* find
* ls
* tree

---

## Notes

* `rmdir` is safer than `rm -r`.
* Only works on empty directories.
* Use `find` to locate empty directories before deleting.

Example:

```bash
find . -type d -empty
```

Delete them:

```bash
find . -type d -empty -delete
```

---

## References

```bash
man rmdir
info rmdir
```

---

## Quick Cheat Sheet

```bash
rmdir folder
rmdir dir1 dir2 dir3
rmdir -p project/src/python
rmdir -v backup
find . -type d -empty
rm -r project
```
