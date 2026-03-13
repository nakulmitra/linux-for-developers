# User Management in Linux (`useradd`, `usermod`, `userdel`)

## 1. Introduction

Linux is designed as a **multi-user operating system**, meaning multiple users can access and work on the same system simultaneously. To manage access and maintain security, Linux provides a **user management system** that allows administrators to:

* Create new users
* Modify existing user accounts
* Delete users when they are no longer needed

These operations are performed using three primary commands:

| Command   | Purpose                 |
| --------- | ----------------------- |
| `useradd` | Create a new user       |
| `usermod` | Modify an existing user |
| `userdel` | Delete a user           |

User management is an essential skill for:

* System Administrators
* DevOps Engineers
* Backend Developers
* Anyone managing Linux servers

# 2. How Linux Stores User Information

Linux stores user account information in several system files.

## `/etc/passwd`

This file contains basic user account details.

Example entry:

```bash
nakul:x:1001:1001:Nakul Mitra:/home/nakul:/bin/bash
```

### Field Explanation

| Field         | Description                                             |
| ------------- | ------------------------------------------------------- |
| nakul         | Username                                                |
| x             | Password placeholder (actual password stored elsewhere) |
| 1001          | User ID (UID)                                           |
| 1001          | Group ID (GID)                                          |
| Nakul Mitra   | User description                                        |
| /home/nakul   | Home directory                                          |
| /bin/bash     | Default login shell                                     |

## `/etc/shadow`

This file stores **encrypted user passwords** and password policies.

Example:

```
nakul:$6$k8...:19000:0:99999:7:::
```

Only the **root user** can read this file for security reasons.

## `/etc/group`

This file stores group information.

Example:

```
developers:x:1002:nakul,piyush
```

This means the users **nakul** and **piyush** belong to the **developers** group.

# 3. Creating Users with `useradd`

## What is `useradd`?

`useradd` is used to **create new user accounts** in the system.

## Basic Syntax

```bash
sudo useradd username
```

Example:

```bash
sudo useradd nakul
```

This creates a user named **nakul**.

However, this command may not automatically create a home directory.

## Creating a User with a Home Directory

To create a home directory automatically:

```bash
sudo useradd -m nakul
```

This creates:

```
/home/nakul
```

The home directory stores:

* personal files
* configuration files
* user environment settings

## Setting a Password

After creating a user, we must assign a password.

```bash
sudo passwd nakul
```

The system will prompt us to enter and confirm a password.

Without a password, the user cannot log in.

## Creating a User with a Specific Shell

Example:

```bash
sudo useradd -m -s /bin/bash nakul
```

This assigns `/bin/bash` as the user's login shell.

# 4. Modifying Users with `usermod`

## What is `usermod`?

`usermod` is used to **modify an existing user account**.

## Basic Syntax

```bash
sudo usermod [options] username
```

## Changing the Home Directory

```bash
sudo usermod -d /home/newnakul nakul
```

This changes the home directory path.

## Adding a User to a Group

```bash
sudo usermod -aG developers nakul
```

### Explanation

| Option | Meaning                  |
| ------ | ------------------------ |
| `-a`   | Append user to group     |
| `-G`   | Specify secondary groups |

> Important, If we run:

```bash
sudo usermod -G developers nakul
```

without `-a`, existing group memberships will be removed.

## Renaming a User

```bash
sudo usermod -l newnakul nakul
```

This renames the user account.

# 5. Deleting Users with `userdel`

## What is `userdel`?

`userdel` removes a user account from the system.

## Basic Syntax

```bash
sudo userdel username
```

Example:

```bash
sudo userdel nakul
```

This deletes the user account but **keeps the home directory**.

## Deleting User with Home Directory

```bash
sudo userdel -r nakul
```

This removes:

* the user account
* the home directory
* the mail spool

# 6. Real-World Developer Scenarios

## 1. Adding a New Developer to a Server

```bash
sudo useradd -m -G developers piyush
sudo passwd piyush
```

This creates a user and adds them to the **developers group**.

## 2. Granting Sudo Access

To allow administrative privileges:

```bash
sudo usermod -aG sudo piyush
```

Now the user can execute commands using `sudo`.

## 3. Removing a Developer from the System

When a team member leaves:

```bash
sudo userdel -r developer1
```

This removes their account and files.

# 7. User IDs (UID)

Every user in Linux has a **unique identifier called UID**.

Typical UID ranges:

| UID Range | Purpose       |
| --------- | ------------- |
| 0         | Root user     |
| 1-999     | System users  |
| 1000+     | Regular users |

We can check UID using:

```bash
id username
```

Example:

```bash
id nakul
```

Output:

```
uid=1001(nakul) gid=1001(nakul) groups=1001(nakul),1002(developers)
```

# 8. Best Practices for User Management

To maintain a secure Linux system:

* Avoid using the **root account directly**
* Create separate users for each developer
* Assign users to groups for shared access
* Remove inactive users
* Use **sudo privileges carefully**

# 9. Common Mistakes

Some common mistakes include:

* Forgetting to set a password after creating a user
* Adding users to groups without `-a` option
* Deleting users without removing their files
* Giving unnecessary sudo access

Proper user management is essential for **security and system stability**.

# 10. Command Summary

| Command                   | Purpose                         |
| ------------------------- | ------------------------------- |
| `useradd username`        | Create new user                 |
| `useradd -m username`     | Create user with home directory |
| `passwd username`         | Set password                    |
| `usermod -aG group user`  | Add user to group               |
| `usermod -l newname user` | Rename user                     |
| `userdel username`        | Delete user                     |
| `userdel -r username`     | Delete user with home directory |

# 11. Conclusion

User management is a fundamental part of Linux administration. Using commands like **useradd**, **usermod**, and **userdel**, administrators can control:

* Who can access the system
* What permissions users have
* How users collaborate within groups

Proper user management ensures:

* system security
* organized access control
* efficient collaboration in multi-user environments

Mastering these commands is essential for anyone working with **Linux servers, DevOps environments, or production systems**.