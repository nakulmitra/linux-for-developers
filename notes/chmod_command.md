# Linux `chmod` Command

In Linux, every file and directory has **access permissions** that define:

* Who can read the file
* Who can modify the file
* Who can execute the file

The `chmod` command (Change Mode) is used to modify these permissions.

It is one of the most important commands for:

* Developers
* DevOps Engineers
* System Administrators
* Backend Engineers working with Linux servers

# Understanding Linux Permission Model

Before understanding `chmod`, we must understand how Linux permissions work. 

Each file has permissions for three categories:

| Category   | Meaning                 |
| ---------- | ----------------------- |
| User (u)   | Owner of the file       |
| Group (g)  | Users in the same group |
| Others (o) | Everyone else           |

Each category can have three types of permissions:

| Permission | Symbol | Meaning             |
| ---------- | ------ | ------------------- |
| Read       | r      | View file content   |
| Write      | w      | Modify file         |
| Execute    | x      | Run file as program |

Example output of `ls -l`:

```
-rwxr-xr--
```

Breakdown:

```
-   -> File type
rwx -> User permissions
r-x -> Group permissions
r-- -> Others permissions
```

# What is `chmod`?

`chmod` stands for:

> **Change Mode:** It modifies the permission bits of a file or directory.

### Syntax

```bash
chmod [options] mode file_name
```

# Two Ways to Use `chmod`

There are two main modes:

1. **Symbolic Mode**
2. **Numeric (Octal) Mode**

# Symbolic Mode

Symbolic mode uses letters:

| Symbol | Meaning              |
| ------ | -------------------- |
| u      | user                 |
| g      | group                |
| o      | others               |
| a      | all                  |
| +      | add permission       |
| -      | remove permission    |
| =      | set exact permission |

### Examples

### Add execute permission to user

```bash
chmod u+x script.sh
```

### Remove write permission from group

```bash
chmod g-w file.txt
```

### Give read permission to all

```bash
chmod a+r file.txt
```

### Set exact permission

```bash
chmod u=rwx,g=rx,o=r file.txt
```

# Numeric (Octal) Mode

This is the most commonly used method in production systems.

Each permission has a numeric value:

| Permission  | Value |
| ----------- | ----- |
| Read (r)    | 4     |
| Write (w)   | 2     |
| Execute (x) | 1     |

We add the values together.

### Example Calculation

| Permission | Calculation | Value |
| ---------- | ----------- | ----- |
| rwx        | 4 + 2 + 1   | 7     |
| rw-        | 4 + 2 + 0   | 6     |
| r-x        | 4 + 0 + 1   | 5     |
| r--        | 4 + 0 + 0   | 4     |

## Common Permission Values

| Numeric | Meaning                        |
| ------- | ------------------------------ |
| 777     | rwxrwxrwx (Full access to all) |
| 755     | rwxr-xr-x (Common for scripts) |
| 744     | rwxr--r--                      |
| 644     | rw-r--r-- (Common for files)   |
| 600     | rw------- (Private file)       |

## Example

```bash
chmod 755 script.sh
```

Breakdown:

* 7 -> User: rwx
* 5 -> Group: r-x
* 5 -> Others: r-x

# Directory Permissions Special Behavior

Permissions behave differently for directories.

| Permission | Meaning in Directory |
| ---------- | -------------------- |
| r          | List files inside    |
| w          | Create/delete files  |
| x          | Enter directory (cd) |

> Important: To access a directory, **execute permission (x) is mandatory**.

# Recursive Permission Change

To change permissions of a directory and all its contents:

```bash
chmod -R 755 project/
```

`-R` means recursive.

> Be careful in production systems.

# Why `chmod 777` is Dangerous

`777` gives:

```
rwxrwxrwx
```

Meaning:

* Anyone can modify
* Anyone can execute
* Anyone can delete

This creates:

* Security vulnerabilities
* Data tampering risk
* Malware execution risk

Never use 777 in production unless absolutely required.

## Real-World Developer Use Cases

### Fix `Permission Denied` Error

```
bash: ./script.sh: Permission denied
```

Solution:

```bash
chmod +x script.sh
```

### Deployment on Linux Server

* Application scripts -> 755
* Configuration files -> 600
* Public web files -> 644

### CI/CD Pipeline Issues

Many build failures happen because:

* Script does not have execute permission
* Git does not track execute bit properly

Fix:

```bash
chmod 755 deploy.sh
```

# Security Best Practices

* Follow principle of least privilege
* Avoid 777
* Use 600 for sensitive files
* Use 755 for executable scripts
* Review permissions during deployment

# Interview Questions

### Q1: Difference between 755 and 644?

* 755 -> Executable
* 644 -> Non-executable

### Q2: Why can't I access a directory even if it has read permission?

Because execute permission is required to enter the directory.

### Q3: What does `chmod -R 777 /` do?

It recursively gives full access to entire filesystem - extremely dangerous.

# Summary

* Linux permissions control file access.
* `chmod` modifies permission bits.
* Two modes: symbolic and numeric.
* Numeric mode is widely used in production.
* Avoid insecure permission settings.

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/linux-permissions.md)