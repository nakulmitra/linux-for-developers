# Searching Inside Files in Linux

### `grep`, `egrep`, and `fgrep`

Searching text inside files is one of the most common tasks performed by developers, DevOps engineers, and system administrators. Linux provides powerful command-line utilities that allow us to quickly find patterns, errors, configuration values, and keywords inside files and directories.

This section explains **grep**, **egrep**, and **fgrep**, how they work, when to use them, and practical real-world examples.

## Why Text Searching Is Important in Linux

In real-world systems, we often need to:

* Debug application errors from log files
* Search configuration values
* Find TODO comments in code
* Locate sensitive strings in large directories
* Monitor system and server logs

Manually opening files is inefficient. Tools like `grep` allow us to **search instantly**, even across thousands of files.

## What Is `grep`?

`grep` stands for **Global Regular Expression Print**.

It scans one or more files, searches for lines matching a given pattern, and prints those lines to standard output.

### Basic Syntax

```bash
grep "pattern" filename
```

### Example

```bash
grep "error" application.log
```

This command searches for the word `error` inside `application.log` and prints all matching lines.

## Common `grep` Options

### Ignore Case (`-i`)

```bash
grep -i "error" application.log
```

Matches `error`, `Error`, `ERROR`, etc.

### Show Line Numbers (`-n`)

```bash
grep -n "error" application.log
```

Helpful for debugging and code reviews.

### Search Multiple Files

```bash
grep "error" *.log
```

### Recursive Search (`-r`)

```bash
grep -r "password" /etc
```

Searches through all files and subdirectories.

> Very useful for scanning configuration files

## Using Regular Expressions with `grep`

`grep` becomes extremely powerful when combined with **regular expressions**.

### Lines Starting With a Word

```bash
grep "^ERROR" app.log
```

### Lines Ending With a Word

```bash
grep "failed$" app.log
```

### Match Digits

```bash
grep "[0-9]" data.txt
```

## What Is `egrep`?

`egrep` is an extended version of `grep` that supports **Extended Regular Expressions (ERE)**.

> On modern Linux systems, `egrep` is equivalent to: `grep -E`

### Match Multiple Patterns

```bash
egrep "error|failed|exception" app.log
```

### Same Using `grep`

```bash
grep -E "error|failed|exception" app.log
```

### Advanced Pattern Example

```bash
egrep "(ERROR|WARN)[0-9]+" app.log
```

## What Is `fgrep`?

`fgrep` performs **fixed-string searches**, meaning it does **not interpret regular expressions**.

> On modern Linux systems, `fgrep` is equivalent to: `grep -F`

### Example

```bash
fgrep "ERROR|WARN" app.log
```

This searches for the **exact string** `ERROR|WARN`.

### When to Use `fgrep`

* Searching literal strings
* Searching text containing special characters
* Performance-sensitive searches on large files

## Comparison: grep vs egrep vs fgrep

| Command | Purpose               | Regex Support | Modern Equivalent |
| ------- | --------------------- | ------------- | ----------------- |
| `grep`  | Basic text search     | Yes           | `grep`            |
| `egrep` | Extended regex search | Yes (ERE)     | `grep -E`         |
| `fgrep` | Fixed string search   | No            | `grep -F`         |

## Practical Developer Use Cases

### Search Errors in Logs

```bash
grep -i "exception" server.log
```

### Search Configuration Values

```bash
grep "server.port" application.properties
```

### Search Across Project Files

```bash
grep -r "TODO" .
```

### Monitor Logs (Combine with tail)

```bash
tail -f app.log | grep "ERROR"
```

## Best Practices

* Use `less` with `grep` for large outputs:

  ```bash
  grep "error" app.log | less
  ```
* Prefer `grep -r` for directory-wide searches
* Use `fgrep` when searching literal strings
* Learn basic regex to unlock full grep power

## Summary

* `grep` is the most important Linux text-search tool
* `egrep` enables advanced pattern matching
* `fgrep` is optimized for exact string searches
* These commands are essential for:

  * Debugging
  * Log analysis
  * Configuration management
  * Codebase exploration

Mastering `grep` dramatically improves productivity for developers and system engineers.

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/view-files.md)