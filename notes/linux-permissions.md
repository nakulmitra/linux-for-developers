# Understanding File Permissions in Linux (r, w, x)

File permissions are one of the most important security features in Linux. They define **who can access a file or directory** and **what actions they are allowed to perform**. Every file and directory in Linux has:

* An **owner**
* A **group**
* A set of **permissions**

These permissions control:

* Who can **read** a file
* Who can **modify** a file
* Who can **execute** a file or enter a directory

Understanding this concept is mandatory for developers, DevOps engineers, and system administrators.

## Why File Permissions Matter

Linux is a **multi-user operating system**. Multiple users can work on the same machine at the same time. Without permissions:

* Any user could modify system files
* Any user could delete critical data
* Any script could run without restrictions

File permissions provide:

* **Security**
* **Isolation between users**
* **Controlled access to system resources**

## The Three Permission Types

Linux uses three basic permission types:

| Symbol | Name    | Meaning for Files            | Meaning for Directories              |
| ------ | ------- | ---------------------------- | ------------------------------------ |
| r      | Read    | View file content            | List directory contents              |
| w      | Write   | Modify file content          | Create/delete files inside directory |
| x      | Execute | Run file as a program/script | Enter the directory (cd)             |

## Viewing File Permissions

To view permissions, use:

```bash
ls -l
```

Example output:

```bash
-rwxr-xr-- 1 nakul users 1024 notes.txt
```

This single line contains **all permission information**.

## Understanding Permission Format

Let's break this down:

```bash
-rwxr-xr--
```

### 1. First Character - File Type

| Symbol | Meaning       |
| ------ | ------------- |
| -      | Regular file  |
| d      | Directory     |
| l      | Symbolic link |

Example:

```bash
drwxr-xr-x
```

This means it is a **directory**.

### 2. Next 9 Characters - Permissions

These are divided into **three groups of three**:

```bash
rwx | r-x | r--
```

| Section | Represents   |
| ------- | ------------ |
| 1st     | Owner (User) |
| 2nd     | Group        |
| 3rd     | Others       |

## Real Meaning Example

Permission string:

```bash
rwxr-xr--
```

Means:

| Entity | Permissions          |
| ------ | -------------------- |
| Owner  | Read, Write, Execute |
| Group  | Read, Execute        |
| Others | Read only            |

## File vs Directory Permissions (Important Concept)

### For Files

| Permission | Effect          |
| ---------- | --------------- |
| r          | Can read file   |
| w          | Can modify file |
| x          | Can run file    |

### For Directories

| Permission | Effect                   |
| ---------- | ------------------------ |
| r          | Can list files           |
| w          | Can create/delete files  |
| x          | Can enter directory (cd) |

This is why sometimes:

* We can see a directory but **cannot enter it**
* We can enter but **cannot create files**

## Common Developer Problem: Permission Denied

Example:

```bash
./deploy.sh
```

Error:

```bash
Permission denied
```

> Reason: The script does **not have execute permission**. Linux will never run a file unless `x` is set.

## Typical Permission Patterns

| Permission | Meaning            |
| ---------- | ------------------ |
| rw-r--r--  | Normal text file   |
| rwxr-xr-x  | Executable program |
| rw-------  | Private file       |
| drwxr-xr-x | Public directory   |
| drwx------ | Private directory  |

## Mental Model (Very Useful)

Think of permissions like, linux asks three questions.

1. Is the user the **owner**?
2. Else, is the user in the **group**?
3. Else, treat as **others**

And then checks:

* Can they **read**?
* Can they **write**?
* Can they **execute**?

## Why Developers Must Understand This

As a developer, file permissions affect:

* Running scripts
* Deploying applications
* Reading config files
* Accessing logs
* Docker volumes
* CI/CD pipelines
* SSH access
* Production servers

Most real-world Linux errors come from **Incorrect permissions, not broken code.**

## Real Production Example

Spring Boot app fails to start:

```bash
./start.sh
Permission denied
```

> Fix: The script exists, but **execute permission missing**. This is not a Java problem. This is a **Linux permission problem**.

## Summary Table

### Permission Symbols

| Symbol | Meaning |
| ------ | ------- |
| r      | Read    |
| w      | Write   |
| x      | Execute |

### Permission Groups

| Group  | Represents    |
| ------ | ------------- |
| Owner  | File creator  |
| Group  | Team access   |
| Others | Everyone else |

## Key Takeaways

* Linux permissions are **fundamental to security**
* Every file has **owner, group, others**
* Every entity has **r, w, x permissions**
* `ls -l` is our first debugging tool
* Most **Permission denied** issues are solved by understanding this topic

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/sort-n-uniq-command.md)