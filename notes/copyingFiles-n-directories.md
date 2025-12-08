# Copying Files and Directories in Linux (`cp` Command)

The `cp` command in Linux is used to **copy files and directories** from one location to another. It is one of the most commonly used file-handling commands and is essential for backup, development work, and general file management in Linux.

This command allows us to:

* Copy individual files
* Copy files into directories
* Copy multiple files at once
* Copy entire folders recursively
* Preserve permissions, timestamps, and attributes (with options)

### Basic Syntax

```
cp [options] source destination
```

* **source:** The file or folder we want to copy
* **destination:** The new file name or location

## Copying a Single File

To copy a file, simply specify the original file and the destination file name:

```
cp notes.txt backup_notes.txt
```

This creates a new file named `backup_notes.txt` containing the same content as `notes.txt`. The original file remains unchanged.

## Copying a File into Another Directory

We can copy a file into a different folder. If the filename is not changed, the original name will be preserved:

```
cp file.txt /home/user/Documents/
```

Linux will place `file.txt` inside the `Documents` directory.

**Tip:** If the directory name ends with a slash `/`, Linux expects it to be a folder.

## Copying Multiple Files

The `cp` command supports copying multiple files in one command:

```
cp file1.txt file2.txt /home/user/backup/
```

This copies both files into the `backup` directory.

## Copying Directories (Recursive Copy)

By default, `cp` **cannot copy directories**. If we try, Linux will return an error:

```
cp projects backup
cp: -r not specified; omitting directory 'projects'
```

To copy a directory and everything inside it (including subdirectories and files), use the `-r` or `--recursive` option:

```
cp -r projects backup_projects
```

This copies the entire `projects` directory and its content.

### Useful Options for `cp`

| Option | Meaning                                   | Example                  |
| ------ | ----------------------------------------- | ------------------------ |
| `-r`   | Copy directories recursively              | `cp -r src backup/`      |
| `-i`   | Interactive mode (ask before overwriting) | `cp -i a.txt b.txt`      |
| `-v`   | Verbose mode (shows what is being copied) | `cp -v file.txt backup/` |
| `-p`   | Preserve file timestamps & permissions    | `cp -p file.txt backup/` |
| `-u`   | Copy only if the source is newer          | `cp -u log.txt backup/`  |

Example combining flags:

```
cp -rvp project/ backup/
```

This will:

* Copy the folder recursively
* Show each file being copied
* Preserve metadata like owner, timestamps, and permissions

## Summary

The `cp` command is essential for file management in Linux. Whether we're backing up configuration files, copying project folders, or organizing development files - the `cp` command provides multiple ways to copy efficiently.

| Task                                     | Command Example                  |
| ---------------------------------------- | -------------------------------- |
| Copy a file                              | `cp file.txt backup.txt`         |
| Copy a file to another directory         | `cp file.txt Documents/`         |
| Copy multiple files                      | `cp file1.txt file2.txt backup/` |
| Copy directories                         | `cp -r src/ backup/`             |
| Copy with details and preserved metadata | `cp -rvp folder/ backup/`        |

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/moving-n-renaming-files-n-directories.md) | [Next Tutorial >](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/deleting-files-n-directories.md)