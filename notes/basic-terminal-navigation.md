# Basic Terminal Navigation in Linux (pwd, ls, cd, cat, less, clear, history)

In the previous section, we explored **Linux distributions** and the **Linux file system structure** - learning what directories like `/home`, `/etc`, and `/usr` represent.

Now, it's time to get hands-on! In this section, we'll open the Linux terminal and start navigating the file system using fundamental commands every developer should know.

[![](https://markdown-videos-api.jorgenkh.no/youtube/DhOb4bLk2t8)](https://youtu.be/DhOb4bLk2t8)

## 1. What is the Terminal?

The **terminal** (or command line interface) is our **direct communication channel** with the Linux operating system. Instead of clicking through folders using a GUI, we can **type commands** to interact with files, directories, and processes. For developers and system administrators, the terminal is an **essential tool** - powerful, fast, and scriptable.

## 2. Navigating the File System

### `pwd` - Print Working Directory

Displays the **current directory path** where we are working.

```bash
pwd
```

**Example output:**

```
/home/nakul
```

This tells us that our terminal is currently inside the `/home/nakul` directory.

### `ls` - List Files and Directories

Lists all files and folders in our current directory.

```bash
ls
```

**Useful options:**

| Option   | Description                                          |
| -------- | ---------------------------------------------------- |
| `ls -l`  | Shows detailed info - permissions, size, date, owner |
| `ls -a`  | Displays hidden files (starting with `.`)            |
| `ls -lh` | Shows human-readable file sizes (KB, MB)             |

**Tip:** When working on projects or servers, `ls -l` is especially useful for checking **file permissions and ownership**.

### `cd` - Change Directory

Used to **move between directories**.

```bash
cd /home/nakul/Documents
```

**Other variations:**

```bash
cd ..      # Go one directory up
cd         # Go back to the home directory
```

**Pro Tip:** Use the **Tab key** for **auto-completion** of directory names - it saves a lot of time!

## 3. Viewing File Content

### `cat` - View Entire File

Used to **display the content of a file**.

```bash
cat notes.txt
```

It will print the full content directly in the terminal.

**Note:** For very large files, `cat` may cause content to scroll off the screen - that's when we use `less`.

### `less` - Scroll Through File Content

Used to view **large files one page at a time**.

```bash
less filename.txt
```

**Navigation inside less:**

| Key      | Action                       |
| -------- | -----------------------------|
| ↑ / ↓    | Scroll line by line          |
| `b`      | Scroll one page up           |
| Spacebar | Scroll one page down         |
| `g`      | Go to the first line of file |
| `G`      | Go to the last line of file  |
| Spacebar | Scroll one page down         |
| `Q`      | Quit and return to terminal  |

**Example:**
View system logs with:

```bash
less /var/log/syslog
```

## 4. Cleaning the Terminal

### `clear` - Clear the Screen

Cleans the terminal window for a fresh start.

```bash
clear
```

**Shortcut:** `Ctrl + L`
Both commands achieve the same result.

## 5. Checking Command History

### `history` - Show Previous Commands

Displays all the commands we've recently used.

```bash
history
```

We can rerun commands from history:

```bash
!!       # Repeats the last command
!45      # Executes command number 45 from the history list
```

This is very helpful when repeating long commands during development or debugging.

## 6. Combining Commands Using Pipes

Linux allows us to **chain commands** using the **pipe operator (|)**.
The output of one command becomes the input of another.

Example:

```bash
ls -l | less
```

This command lists files in long format (`ls -l`) and **pipes** the output to `less`, so we can scroll through it easily.

## Summay

| Task                   | Command                    |
| ---------------------- | -------------------------- |
| Show current directory | `pwd`                      |
| List files             | `ls`, `ls -l`, `ls -a`     |
| Change directory       | `cd`, `cd ..`, `cd`        |
| View file content      | `cat`, `less`              |
| Clear terminal         | `clear`, `Ctrl + L`        |
| View command history   | `history`, `!!`, `!number` |
| Combine commands       | `\|`                       |

These commands are the **foundation** of working efficiently in Linux. We'll use them daily whether managing servers, deploying apps, or navigating project directories.

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/linux-setup.md)