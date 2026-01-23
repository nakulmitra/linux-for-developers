# Sorting & Filtering in Linux (`sort`, `uniq`)

This section explains two powerful Linux text-processing commands **`sort`** and **`uniq`** which are widely used by developers, DevOps engineers, and system administrators when working with logs, configuration files, CSV data, and large text datasets.

These commands are commonly used together in Linux pipelines to organize and clean data efficiently.

[![](https://markdown-videos-api.jorgenkh.no/youtube/p11n_ao982I)](https://youtu.be/p11n_ao982I)

## Objectives

After reading this section, you will understand:

* What `sort` does and how to use it
* The difference between alphabetical and numeric sorting
* How to save sorted output to a file
* Why `uniq` requires sorted input
* How to remove duplicates using `uniq`
* How to count duplicate occurrences
* How to combine `grep`, `sort`, and `uniq` in real-world scenarios

# Understanding the `sort` Command

The `sort` command is used to arrange lines of text in a file in a specific order.

By default, it sorts **alphabetically (lexicographically)** line by line.

### Basic Usage

```bash
sort names.txt
```

This command:

* Reads `names.txt`
* Sorts each line alphabetically
* Prints the sorted result to the terminal

> Important: It does **not modify the original file** unless we redirect the output.

## Common `sort` Options

### Reverse Sorting (`-r`)

To sort in reverse (descending) order:

```bash
sort -r names.txt
```

Example:

```
Before:
apple
banana
mango

After sort -r:
mango
banana
apple
```

### Numeric Sorting (`-n`)

By default, numbers are treated as **strings**, which leads to incorrect ordering.

Example file `numbers.txt`:

```
10
2
30
5
```

If we run:

```bash
sort numbers.txt
```

Output will be:

```
10
2
30
5
```

This is incorrect.

Correct way:

```bash
sort -n numbers.txt
```

Output:

```
2
5
10
30
```

This sorts based on numeric value.

### Save Sorted Output to a File

We can store sorted data in a new file:

```bash
sort data.txt > sorted_data.txt
```

Now `sorted_data.txt` contains the sorted content.

# Understanding the `uniq` Command

The `uniq` command is used to remove duplicate lines from a file.

### Important Rule

**The input must be sorted first** Otherwise, `uniq` will not remove all duplicates correctly.

## Basic Example

```bash
sort data.txt | uniq
```

This pipeline:

1. Sorts the file
2. Removes duplicate lines

## Useful `uniq` Options

### Count Duplicates (`-c`)

```bash
sort data.txt | uniq -c
```

Example output:

```
3 ERROR: Connection failed
2 WARNING: Low memory
1 INFO: Server started
```

This tells us:

* How many times each line appears.

### Show Only Duplicate Lines (`-d`)

```bash
sort data.txt | uniq -d
```

This prints only lines that appear more than once.

### Show Only Unique Lines (`-u`)

```bash
sort data.txt | uniq -u
```

This prints only lines that appear **once**.

# Real Developer Use Case

### Count Occurrences of Errors in Logs

Suppose we have an application log file `app.log` and want to count how many times each error appears.

Run:

```bash
grep "ERROR" app.log | sort | uniq -c
```

This does the following:

1. `grep "ERROR"` -> extracts only error lines
2. `sort` -> groups identical lines together
3. `uniq -c` -> counts how many times each error appears

Example output:

```
10 ERROR: Database timeout
5 ERROR: Null pointer exception
2 ERROR: Connection refused
```

This is extremely useful for debugging production systems.

# Summary Table

| Command   | Purpose                   | Example                 |
| --------- | ------------------------- | ----------------------- |
| `sort`    | Sort lines alphabetically | `sort file.txt`         |
| `sort -n` | Numeric sort              | `sort -n numbers.txt`   |
| `uniq`    | Remove duplicates         | `sort file.txt uniq`    |
| `uniq -c` | Count duplicates          | `sort file.txt uniq -c` |

# Key Takeaways

* `sort` helps organize data
* `uniq` removes duplicate lines
* `uniq` only works properly if input is sorted
* These commands are extremely powerful when combined with `grep` and pipes
* They are essential for log analysis, debugging, and data processing in Linux

[< Previous Tutorial](https://github.com/nakulmitra/linux-for-developers/blob/master/notes/wc-command.md)