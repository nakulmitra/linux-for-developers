# **Moving and Renaming Files & Directories in Linux (`mv` Command)**

The `mv` command in Linux is one of the most commonly used file-management commands. It is used for **moving files**, **moving directories**, and **renaming files or directories**. Unlike some commands that have separate operations for different tasks, `mv` performs both *move* and *rename* operations depending on how it is used.

## 1. What Is the `mv` Command?

The name **mv** stands for **move**. In Linux, moving a file is essentially changing its location in the filesystem. Internally, this may involve updating filesystem pointers or physically writing the file to a new location, depending on whether the move happens within the same disk or across different devices.

In addition, the same command is also used for **renaming** files. If the destination we provide is a **file name** instead of a directory, Linux interprets the action as a rename operation.

## 2. Basic Syntax

```bash
mv [options] source destination
```

### **Parameters**

* **source** - the file or directory we want to move or rename
* **destination** - where we want to move it, or the new name we want to assign

## 3. Moving Files

To move a file into another directory:

```bash
mv notes.txt Documents/
```

This command moves the file `notes.txt` from the current directory into the `Documents` directory.

### How It Works:

* Linux checks whether the destination is an **existing directory**.
* If yes -> the source file is moved **into** that folder.

## 4. Moving Directories

We can also move entire folders, including all their contents:

```bash
mv projects/ backup/
```

This will move the entire `projects` directory inside the `backup` directory.

### Key Points:

* Linux moves directories recursively.
* No need for any extra option like `-r` (required for cp but **not** for mv).

## 5. Renaming Files or Directories

The `mv` command is also used for renaming:

```bash
mv oldname.txt newname.txt
```

### How Linux Determines This Is a Rename:

* If the destination **does not exist** as a directory,
* And the destination is treated as a **new filename**,
* Then Linux performs a **rename** instead of a move.

We can rename directories the same way:

```bash
mv oldfolder newfolder
```

## 6. Moving Multiple Files at Once

We can move several files in one command:

```bash
mv file1.txt file2.txt /home/nakul/Documents
```

Here:

* `file1.txt` and `file2.txt` are the sources
* `/home/nakul/Documents` is the destination directory

This is useful when organizing related files into a single folder.

## 7. Important Behavior of `mv`

### Overwrites by Default

If the destination file already exists, `mv` will overwrite it **without asking**.

To prevent accidental overwrites, use:

```bash
mv -i file.txt target.txt
```

The `-i` option (interactive) asks for confirmation.

### Moving Across Filesystems

If the move happens within the **same filesystem**, Linux simply updates metadata (fast operation).

If moved **across different partitions or devices**, Linux internally:

* Copies the file to the new destination
* Deletes the original file
  (so this takes more time)

### No Copy Is Created

`mv` always **moves** files - it does not leave a copy behind.

If we want to copy instead of move, use the `cp` command.

## 8. Useful Options

| Option | Description                              | Example               |
| ------ | ---------------------------------------- | --------------------- |
| `-i`   | Interactive mode (asks before overwrite) | `mv -i a.txt b.txt`   |
| `-f`   | Force move without warning               | `mv -f file.txt dir/` |
| `-v`   | Verbose — shows what is being moved      | `mv -v a.txt dir/`    |
| `-n`   | No overwrite                             | `mv -n a.txt b.txt`   |

## 9. Practical Examples

### Move a file to parent directory:

```bash
mv file.txt ..
```

### Move all `.log` files:

```bash
mv *.log logs/
```

### Rename with spaces (use quotes):

```bash
mv "old name.txt" "new name.txt"
```

## 10. Summary Table

| Command             | Purpose                      | Example                        |
| ------------------- | ---------------------------- | ------------------------------ |
| Move file           | Move a file into a directory | `mv file.txt Documents/`       |
| Move directory      | Move entire folder           | `mv projects/ backup/`         |
| Rename file         | Rename file using mv         | `mv old.txt new.txt`           |
| Move multiple files | Move many files at once      | `mv a.txt b.txt c.txt backup/` |
| Prevent overwrite   | Safe move                    | `mv -i file.txt dir/`          |

## **Conclusion**

The `mv` command is an essential part of Linux file management.
With just one command, we can:

* Move files
* Move directories
* Rename files
* Rename directories
* Move multiple files at once

Understanding `mv` makes file organization faster, more flexible, and more efficient in the Linux terminal.