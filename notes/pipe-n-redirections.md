# Combining Commands with Pipes & Redirection in Linux

## 1. Introduction

Linux is powerful not just because of its commands, but because of how **commands can be combined together**. Instead of writing complex programs, we can solve real-world problems by chaining simple commands using:

* **Pipes (`|`)**
* **Redirection (`>`, `>>`, `<`)**

This is a core concept used by:

* Developers
* DevOps Engineers
* System Administrators

# 2. What is a Pipe (`|`)?

A **pipe (`|`)** takes the output of one command and passes it as input to another command.

## Basic Syntax

```bash
command1 | command2
```

## Example

```bash
ls | wc -l
```

### Explanation:

* `ls` -> Lists files
* `wc -l` -> Counts lines

> Output: Total number of files in the directory

## Another Example

```bash
cat app.log | grep "ERROR"
```

* `cat` reads the file
* `grep` filters lines containing "ERROR"

## Better Approach (Best Practice)

Avoid unnecessary use of `cat`:

```bash
grep "ERROR" app.log
```

# 3. Chaining Multiple Commands

We can chain multiple commands using pipes.

## Example

```bash
grep "ERROR" app.log | sort | uniq -c
```

### What happens step-by-step:

1. `grep` → Finds lines containing "ERROR"
2. `sort` → Sorts the lines
3. `uniq -c` → Counts duplicate occurrences

> This is commonly used for **log analysis**

# 4. Output Redirection (`>`)

Output redirection sends command output to a file instead of the terminal.

## Syntax

```bash
command > file
```

## Example

```bash
ls > files.txt
```

> Saves the list of files into `files.txt`

## Important Behavior

* If the file exists -> **it will be overwritten**

# 5. Append Output (`>>`)

To append output instead of overwriting, use `>>`.

## Syntax

```bash
command >> file
```

## Example

```bash
echo "New log entry" >> app.log
```

> Adds new content at the end of the file

## Difference Between `>` and `>>`

| Operator | Behavior        |
| -------- | --------------- |
| `>`      | Overwrites file |
| `>>`     | Appends to file |

# 6. Input Redirection (`<`)

Input redirection allows a command to take input from a file instead of the keyboard.

## Syntax

```bash
command < file
```

## Example

```bash
wc -l < file.txt
```

> Counts lines using input from the file

## Note

* Less commonly used compared to pipes
* Still important for understanding Linux I/O behavior

# 7. Standard Streams in Linux

To understand pipes and redirection, we must know about **standard streams**:

| Stream     | Description |
| ---------- | ----------- |
| STDIN (0)  | Input       |
| STDOUT (1) | Output      |
| STDERR (2) | Error       |

## Example

```bash
ls > output.txt
```

* STDOUT goes to file instead of terminal

# 8. Real-World Developer Examples

## 1. Count Errors in Logs

```bash
grep "ERROR" app.log | wc -l
```

## 2. Save Filtered Output

```bash
grep "ERROR" app.log > errors.txt
```

## 3. Append Logs

```bash
echo "Server restarted" >> app.log
```

## 4. Count Files in Directory

```bash
ls | wc -l
```

## 5. Full Pipeline Example

```bash
grep "ERROR" app.log | sort | uniq -c > summary.txt
```

> Creates a summarized report of errors

# 9. Advanced Redirection (Bonus)

## Redirect Errors

```bash
command 2> error.txt
```

> Saves error messages

## Redirect Output & Error Together

```bash
command > output.txt 2>&1
```

## Discard Output

```bash
command > /dev/null
```

> Output is ignored

# 10. Best Practices

* Avoid unnecessary `cat` usage
* Use pipes to simplify workflows
* Be careful with `>` (it overwrites data)
* Use `>>` for logs and append operations
* Combine commands for efficiency

# 11. Common Mistakes

* Overwriting important files accidentally
* Using `cat` unnecessarily
* Not understanding command order in pipelines
* Ignoring error output

# 12. Summary

| Symbol | Meaning                     |
| ------ | --------------------------- |
| `>`    | Redirect output (overwrite) |
| `>>`   | Append output               |
| `<`    | Take input from file        |

# 13. Interview Questions

### Q1: What is a pipe in Linux?

A pipe connects the output of one command to the input of another.

### Q2: What is the difference between `>` and `>>`?

* `>` → Overwrites file
* `>>` → Appends to file

### Q3: What does this command do?

```bash
grep "ERROR" app.log | wc -l
```

Counts number of lines containing "ERROR".

### Q4: What are standard streams?

* STDIN -> Input
* STDOUT -> Output
* STDERR -> Errors

# 14. Conclusion

Pipes and redirection are among the most powerful features of Linux.

They allow us to:

* Combine simple commands into complex workflows
* Process large datasets efficiently
* Automate repetitive tasks
* Perform real-time log analysis

Mastering these concepts will significantly improve our productivity as a developer or DevOps engineer.