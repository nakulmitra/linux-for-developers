# Most Used Linux Commands for Developers (Everyday Use)

## Introduction

Linux is the backbone of modern software development. From local development environments to production servers and cloud infrastructure, Linux is everywhere.

As a developer, we don’t need to memorize hundreds of commands but we **must master a core set of commands** that we’ll use daily for:

* Navigating the file system
* Managing files and directories
* Viewing and debugging logs
* Searching data efficiently
* Monitoring and managing processes
* Handling permissions

This guide covers the **most practical Linux commands** used in real-world development and interviews.

[![](https://markdown-videos-api.jorgenkh.no/youtube/ytvNlh-nrFw)](https://youtu.be/ytvNlh-nrFw)

## Why Developers Must Learn Linux Commands

Linux commands allow us to:

* Work faster than GUI-based tools
* Debug issues directly on servers
* Manage files efficiently
* Analyze logs and data
* Automate repetitive tasks

> In backend and DevOps roles, Linux is not optional — it’s essential.

# 1. File & Directory Management Commands

## `ls` — List Files and Directories

### Syntax

```bash
ls [options]
```

### Examples

```bash
ls
ls -l
ls -a
```

### Explanation

* `ls` → basic listing
* `-l` → detailed view (permissions, owner, size)
* `-a` → includes hidden files

## `cd` — Change Directory

```bash
cd /home/user/project
cd ..
cd ~
```

* `..` → move one level up
* `~` → home directory

## `pwd` — Present Working Directory

```bash
pwd
```

> Shows the current directory path

## `mkdir` — Create Directory

```bash
mkdir project
mkdir -p src/main/java
```

* `-p` → create nested directories

## `rm` — Remove Files and Directories

```bash
rm file.txt
rm -r folder/
rm -rf folder/
```

**Warning**

* No recycle bin in Linux
* `-rf` can delete everything permanently

# 2. File Viewing & Editing Commands

## `cat` — View File Content

```bash
cat file.txt
```

> Best for small files

## `less` — View Large Files

```bash
less logfile.log
```

### Controls

* `q` → quit
* `/text` → search

> Ideal for large logs

## `head` — View First Lines

```bash
head -n 10 file.txt
```

## `tail` — View Last Lines

```bash
tail -n 10 file.txt
```

## Real-World: Live Log Monitoring

```bash
tail -f application.log
```

> Shows logs in real time (widely used in production)

# 3. Search & Filtering Commands

## `grep` — Search Text

```bash
grep "error" logfile.log
grep -i "error" logfile.log
grep -r "TODO" .
```

* `-i` → case insensitive
* `-r` → recursive search

## Real-Time Log Filtering

```bash
tail -f logfile.log | grep "ERROR"
```

> Monitor only error logs live

## `find` — Search Files

```bash
find . -name "file.txt"
find / -type f -name "*.log"
```

> Powerful file search tool

# 4. Process & System Commands

## `ps` — Process Snapshot

```bash
ps
ps -ef
```

> Shows running processes

## `top` — Real-Time Monitoring

```bash
top
```

> Displays:

* CPU usage
* Memory usage
* Running processes

## `kill` — Stop a Process

```bash
kill <PID>
kill -9 <PID>
```

* Default → graceful stop
* `-9` → force kill

# 5. Permissions & Ownership

## `chmod` — Change Permissions

```bash
chmod +x script.sh
chmod 755 script.sh
```

> Controls read, write, execute access

## `chown` — Change Ownership

```bash
chown user:user file.txt
```

> Changes file owner

# 6. Productivity Commands

## `history` — Command History

```bash
history
```

> Shows previously executed commands

## `clear` — Clear Terminal

```bash
clear
```

# Real-World Developer Workflows

## 1. Debugging Logs

```bash
tail -f app.log | grep "ERROR"
```

> Monitor only errors in real time

## 2. Finding Files in Project

```bash
find . -name "*.java"
```

## 3. Killing a Stuck Application

```bash
ps -ef | grep java
kill <PID>
```

## 4. Counting Errors

```bash
grep "ERROR" app.log | wc -l
```

# Interview Preparation Tips

Focus on these commands:

### File Management

* `ls`, `cd`, `rm`, `mkdir`

### File Viewing

* `cat`, `less`, `head`, `tail`

### Searching

* `grep`, `find`

### Process Management

* `ps`, `top`, `kill`

### Permissions

* `chmod`, `chown`

> These are **frequently asked in interviews**

# Best Practices

* Always double-check before using `rm -rf`
* Use `less` instead of `cat` for large files
* Prefer `grep` for quick filtering
* Avoid force killing (`kill -9`) unless necessary
* Use pipelines (`|`) to combine commands

# Quick Summary Table

| Category        | Commands                         |
| --------------- | -------------------------------- |
| File Management | `ls`, `cd`, `pwd`, `mkdir`, `rm` |
| File Viewing    | `cat`, `less`, `head`, `tail`    |
| Search          | `grep`, `find`                   |
| Process         | `ps`, `top`, `kill`              |
| Permissions     | `chmod`, `chown`                 |
| Productivity    | `history`, `clear`               |

# Conclusion

Mastering these Linux commands will:

* Boost our productivity
* Improve debugging skills
* Help us work confidently on servers
* Prepare us for technical interviews

> These are not just commands, they are **daily tools for developers**.

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/manage-process.md)