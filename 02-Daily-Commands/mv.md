# mv — Move and Rename Files or Directories

## Purpose

The `mv` command stands for **Move**.

It is used to:

1. Move files from one location to another.
2. Move directories from one location to another.
3. Rename files and directories.

Unlike `cp`, the source file or directory is removed from its original location after the operation.

When moving files within the same filesystem, `mv` is extremely fast because it only updates filesystem metadata instead of copying the actual file contents.

---

## Syntax

```bash
mv [options] source destination
```

---

## Common Options

| Option                     | Description                            |
| -------------------------- | -------------------------------------- |
| `mv old_name new_name`     | Rename a file or directory             |
| `mv file /directory/`      | Move file to another directory         |
| `mv -i source destination` | Ask before overwriting existing files  |
| `mv -v source destination` | Display detailed operation information |
| `mv -n source destination` | Never overwrite existing files         |
| `mv -u source destination` | Move only if source is newer           |

---

## Examples

### Example 1: Rename a File

```bash
mv report.txt report_v2.txt
```

Before:

```text
report.txt
```

After:

```text
report_v2.txt
```

The file name changes without modifying its contents.

---

### Example 2: Move a File

```bash
mv report.txt Documents/
```

Before:

```text
report.txt
Documents/
```

After:

```text
Documents/
└── report.txt
```

The file is moved into the Documents directory.

---

### Example 3: Rename a Directory

```bash
mv old_project new_project
```

Before:

```text
old_project/
```

After:

```text
new_project/
```

The directory name changes while preserving its contents.

---

### Example 4: Interactive Move

```bash
mv -i config.conf /etc/myapp/
```

Output:

```text
mv: overwrite '/etc/myapp/config.conf'?
```

The system asks for confirmation before replacing the existing file.

---

### Example 5: Verbose Move

```bash
mv -v app.log archive/
```

Output:

```text
renamed 'app.log' -> 'archive/app.log'
```

Useful for automation scripts and troubleshooting.

---

## Common Use Cases

### 1. Rename a File

```bash
mv report.txt report_v2.txt
```

Useful when creating new versions of files.

---

### 2. Move Files to Another Directory

```bash
mv report.txt ~/Documents/
```

Used for organizing files and folders.

---

### 3. Archive Old Log Files

```bash
mv *.log archive/
```

Common in server administration.

---

### 4. Rename Build Outputs

```bash
mv app app_v1.0
```

Useful during software releases.

---

### 5. Move Processed Files

```bash
mv data.csv done/
```

Frequently used in automation scripts.

---

### 6. Prevent Accidental Overwrites

```bash
mv -i file.txt backup/
```

Recommended for production environments.

---

### 7. Batch Rename Files

```bash
for f in *.log
do
    mv "$f" "archive_$f"
done
```

Example:

Before:

```text
server.log
app.log
error.log
```

After:

```text
archive_server.log
archive_app.log
archive_error.log
```

---

### 8. Rename a Project Directory

```bash
mv old_project new_project
```

Useful when restructuring projects.

---

### 9. Move Multiple Files

```bash
mv file1.txt file2.txt file3.txt backup/
```

Move several files simultaneously.

---

### 10. Organize Downloads

```bash
mv *.pdf Documents/
```

Move all PDF files into a dedicated folder.

---

## Important Options Explained

### Interactive Mode (-i)

```bash
mv -i file.txt backup/
```

Prompts before overwriting files.

Recommended when working with important data.

---

### Verbose Mode (-v)

```bash
mv -v file.txt backup/
```

Displays exactly what was moved.

Useful for debugging scripts.

---

### No Overwrite Mode (-n)

```bash
mv -n file.txt backup/
```

Prevents replacement of existing files.

---

### Update Mode (-u)

```bash
mv -u report.txt backup/
```

Moves only if the source file is newer.

Useful for synchronization tasks.

---

## Difference Between mv and cp

| Feature                | mv      | cp     |
| ---------------------- | ------- | ------ |
| Renames files          | Yes     | No     |
| Moves files            | Yes     | No     |
| Creates duplicate copy | No      | Yes    |
| Removes source         | Yes     | No     |
| Used for backups       | Limited | Common |

---

## Common Interview Questions

### Q1. What is the difference between `mv` and `cp`?

`mv` moves or renames files.

`cp` creates a duplicate copy while keeping the original.

---

### Q2. Does `mv` copy file contents?

Within the same filesystem, usually no.

Linux only updates filesystem metadata, making the operation very fast.

---

### Q3. How do you rename a file?

```bash
mv oldname.txt newname.txt
```

---

### Q4. How do you prevent overwriting files?

```bash
mv -i source destination
```

or

```bash
mv -n source destination
```

---

### Q5. Can `mv` rename directories?

Yes.

```bash
mv old_directory new_directory
```

---

## Related Commands

* cp
* rm
* find
* rsync
* rename

---

## Notes

* `mv` is one of the most frequently used Linux commands.
* Renaming and moving use the same command.
* Always use `-i` when working with important production files.
* Verify moved files using `ls` after the operation.

---

## References

```bash
man mv
info mv
```

---

## Quick Cheat Sheet

```bash
mv file.txt backup/
mv report.txt report_v2.txt
mv -i file.txt destination/
mv -v file.txt destination/
mv -n file.txt destination/
mv -u file.txt destination/
mv *.log archive/
mv old_project new_project
```
