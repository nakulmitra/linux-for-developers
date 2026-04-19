# Change Ownership & Groups in Linux (`chown`, `chgrp`)

In Linux, access control is based on two core concepts:

* **Permissions** (r, w, x)
* **Ownership** (User & Group)

[![](https://markdown-videos-api.jorgenkh.no/youtube/uHiXGcBEIQ8)](https://youtu.be/uHiXGcBEIQ8)

While `chmod` controls *what actions are allowed*, `chown` and `chgrp` control *who those permissions apply to*.

Understanding ownership is critical for:

* Backend Developers
* DevOps Engineers
* System Administrators
* Cloud Engineers
* Anyone managing Linux servers

# Linux File Ownership Model

Every file and directory in Linux has:

* **One Owner (User)**
* **One Group**

We can check ownership using:

```bash
ls -l
```

Example output:

```bash
-rw-r--r-- 1 nakul developers 1024 config.txt
```

### Breakdown:

| Field        | Meaning      |
| ------------ | ------------ |
| `nakul`      | Owner (User) |
| `developers` | Group        |

This means:

* The file belongs to user `nakul`
* It belongs to group `developers`
* Permissions apply differently to:

  * Owner
  * Group members
  * Others

# Why Ownership Matters

Ownership determines:

* Who can modify files
* Who can deploy applications
* Who can access configuration files
* Who can execute scripts

Even if permissions allow access, incorrect ownership can still cause:

```
Permission denied
```

# The `chown` Command

## What is `chown`?

`chown` stands for **Change Owner**

It is used to change:

* File owner
* Or both owner and group

## Basic Syntax

```bash
chown newuser filename
```

## Example: Change Owner

```bash
sudo chown dev file.txt
```

This changes:

* Owner -> dev
* Group remains unchanged

> We usually need `sudo` because only root can change ownership.

# Changing Owner and Group Together

We can modify both in one command:

```bash
sudo chown dev:developers file.txt
```

Meaning:

| Component | Value      |
| --------- | ---------- |
| Owner     | dev        |
| Group     | developers |

This is very common in server environments.

# The `chgrp` Command

## What is `chgrp`?

`chgrp` stands for **Change Group**

It modifies only the group ownership.

## Basic Syntax

```bash
chgrp newgroup filename
```

## Example

```bash
sudo chgrp developers file.txt
```

This:

* Keeps the same owner
* Changes only the group

# Recursive Ownership Changes

To change ownership of a directory and all its contents:

```bash
sudo chown -R dev:developers myproject/
```

`-R` -> Recursive

This affects:

* Directory
* Subdirectories
* All files inside

> Be extremely careful when using `-R` in system directories.

# Real-World Developer Scenarios

## Web Server Permission Issue

Suppose our app is deployed but fails because:

* Web server runs as user `www-data`
* Files are owned by `nakul`

Fix:

```bash
sudo chown -R www-data:www-data myapp/
```

Now:

* Web server owns the files
* Application works properly

## Team Collaboration

Multiple developers need access:

```bash
sudo chown :developers project/
```

Notice:

* Owner remains same
* Group changes to `developers`
* All group members now get access (based on permissions)

## CI/CD Deployment Failures

Build pipelines often fail because:

* Files are created by root
* App runs under non-root user

Fix by assigning proper ownership:

```bash
sudo chown -R appuser:appgroup /var/www/app
```

# Relationship Between Ownership & Permissions

Ownership works together with permissions.

Example:

```bash
-rwxr-xr--
```

Permissions apply as:

* Owner -> rwx
* Group -> r-x
* Others -> r--

If user is:

* Owner -> first permission block applies
* In same group -> second block applies
* Neither -> third block applies

# Security Best Practices

* Follow principle of least privilege
* Avoid running apps as root
* Assign proper group ownership for teams
* Avoid unnecessary recursive changes
* Audit ownership during deployment

# Common Mistakes

* Using `chmod 777` instead of fixing ownership
* Changing ownership of system directories accidentally
* Forgetting `-R` during deployment
* Running production apps as root

# Difference Between `chown` and `chgrp`

| Command                 | Purpose              |
| ----------------------- | -------------------- |
| `chown user file`       | Change owner         |
| `chown user:group file` | Change owner & group |
| `chgrp group file`      | Change group only    |

# Interview Questions

### Q1: Why do we need sudo for chown?

Because only root can change file ownership.

### Q2: What happens if ownership is wrong but permissions are correct?

Access may still fail because the wrong permission block applies.

### Q3: What does `chown -R` do?

Recursively changes ownership of directory and all contents.

### Q4: Difference between `chmod` and `chown`?

* `chmod:` Changes permission bits
* `chown:` Changes file owner
* `chgrp:` Changes file group

# Summary

* Every file in Linux has:

  * One owner
  * One group
* Ownership determines how permissions apply.
* `chown` changes owner.
* `chgrp` changes group.
* Recursive changes must be used carefully.
* Proper ownership is critical for secure deployments.

# Conclusion

Understanding ownership and groups is essential for

* Fixing production permission errors
* Managing Linux servers
* Secure DevOps practices
* Backend deployment pipelines

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/chmod_command.md) | [Next Tutorial >](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/create-modify-update-user.md)