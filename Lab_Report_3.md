
# Lab Report 3 - Bugs and Commands

## Part 1 - Bugs

### Failure-inducing Input

```java
@Test
public void testForFailure() {
    // Assuming there's a bug in the method `buggyMethod` which does not handle zero correctly.
    int result = ExampleClass.buggyMethod(0);
    assertEquals("Expected output for 0", expectedResult, result);
}
```

### Non-Failure-Inducing Input

```java
@Test
public void testForSuccess() {
    // Assuming the method works correctly for inputs other than zero.
    int result = ExampleClass.buggyMethod(5);
    assertEquals("Expected output for 5", expectedResult, result);
}
```

### Symptom
Since we cannot run the JUnit tests, I'll describe a hypothetical symptom:

The symptom observed when running the `testForFailure` is an `AssertionError` indicating that the expected output does not match the actual output when the input is 0.

(Screenshot placeholder)

### The Bug

```java
// Before
public int buggyMethod(int input) {
    return 10 / input;
}
```

```java
// After
public int buggyMethod(int input) {
    if (input == 0) return 0; // handle zero case
    return 10 / input;
}
```

### Description of the Fix
The fix addresses the issue by checking if the input is zero and handling this specific case to avoid a division by zero error, which was the cause of the failure.

## Part 2 - Researching Commands

### Command: `grep`

#### Option 1: `-i` (Ignore case)

```bash
grep -i "pattern" ./technical/file.txt
```
*Output:* (Hypothetical output showing matched lines regardless of case)

The `-i` option is useful when the case sensitivity of the search pattern is not important. It can help find matches regardless of whether they are uppercase or lowercase.

```bash
grep -i "example" ./technical/report.md
```
*Output:* (Hypothetical output showing all occurrences of "example" in any case)

This command searches for the word "example" in a markdown file, ignoring the case, which is useful for case-insensitive searching.

#### Option 2: `-r` (Recursive search)

```bash
grep -r "pattern" ./technical/
```
*Output:* (Hypothetical output showing files and matched lines containing "pattern")

The `-r` option allows for a recursive search through directories, which is useful for finding occurrences of a pattern within all files in a directory tree.

```bash
grep -r "TODO" ./technical/projects/
```
*Output:* (Hypothetical output showing all TODO comments in the projects directory)

This command is handy for developers who want to locate all TODO comments within their project files.

#### Option 3: `-v` (Invert match)

```bash
grep -v "pattern" ./technical/config.cfg
```
*Output:* (Hypothetical output showing all lines that do not match "pattern")

Using the `-v` option inverts the match, displaying all lines that do not contain the pattern, which can be useful for filtering content.

```bash
grep -v "debug" ./technical/logs/logfile.log
```
*Output:* (Hypothetical output excluding lines with the word "debug")

This can be used to exclude specific entries, such as debug messages, from log files.

#### Option 4: `-c` (Count)

```bash
grep -c "pattern" ./technical/data.csv
```
*Output:* (Hypothetical output showing the number of lines that match "pattern")

The `-c` option counts the number of lines containing the pattern, which is useful for summarizing how many times a pattern appears in a file.

```bash
grep -c "error" ./technical/logs/errors.log
```
*Output:* (Hypothetical output with the number of error messages)

This command helps quickly identify the number of error messages in a log file.

### Sources
The information about `grep` command options was sourced from the man pages accessible via the command `man grep` on Unix-like systems and from online resources such as GNU documentation.
