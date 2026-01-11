# Counting Lines, Words & Characters in Linux (`wc`)

The `wc` command is one of the simplest yet most powerful text-processing tools in Linux.
It is used to count **lines, words, and characters** in files or command output. Developers, system administrators, and DevOps engineers use it daily to analyze logs, datasets, and source code.

## What is `wc`?

`wc` stands for **Word Count**, but it does much more than just counting words.

By default, `wc` shows:

* Number of **lines**
* Number of **words**
* Number of **bytes (characters)**
* The **file name**

### Basic Syntax

```bash
wc [options] file
```

## Basic Usage

```bash
wc file.txt
```

Example output:

```
  120   950   6840   file.txt
```

This means:

* `120` -> lines
* `950` -> words
* `6840` -> characters (bytes)

## Counting Only Lines (`-l`)

```bash
wc -l file.txt
```

This prints only the number of lines.

### Common Use Cases

* Count log entries
* Count rows in CSV files
* Measure size of code files

Example:

```bash
grep "ERROR" server.log | wc -l
```

Counts how many error messages appear in the log.

## Counting Words (`-w`)

```bash
wc -w file.txt
```

This counts how many words are present.

### Use Cases

* Analyzing documents
* Counting records in structured text
* Checking size of documentation

## Counting Characters (`-c` and `-m`)

```bash
wc -c file.txt
```

Counts total number of bytes.

```bash
wc -m file.txt
```

Counts actual characters (important for Unicode text).

Use `-m` when working with:

* UTF-8
* Multilingual text
* Special symbols

## Using `wc` with Pipes

`wc` becomes extremely powerful when combined with other Linux commands using pipes (`|`).

### Count matching lines

```bash
grep "ERROR" app.log | wc -l
```

### Count files in a directory

```bash
ls | wc -l
```

### Count number of running processes

```bash
ps aux | wc -l
```

## Counting Multiple Files

```bash
wc file1.txt file2.txt
```

Output:

```
  20   150   900   file1.txt
  30   200   1200  file2.txt
  50   350   2100  total
```

Linux automatically shows a **total** at the bottom.

## Why Developers Use `wc`

`wc` is extremely useful for:

* Checking log volume
* Counting data rows
* Measuring file sizes
* Monitoring pipelines
* Validating scripts
* Estimating codebase size

It is widely used in:

* DevOps
* Backend development
* Data processing
* Shell scripting

## Summary Table

| Command | Purpose                    |
| ------- | -------------------------- |
| `wc`    | Lines, words, characters   |
| `wc -l` | Count lines                |
| `wc -w` | Count words                |
| `wc -c` | Count bytes                |
| `wc -m` | Count characters (Unicode) |

## Final Notes

Although `wc` looks simple, it is one of the most powerful **Linux text analysis tools** when combined with commands like `grep`, `cat`, `sort`, and `uniq`. This makes it an essential skill for every Linux user, developer, and DevOps engineer.