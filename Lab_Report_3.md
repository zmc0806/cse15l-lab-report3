# Lab Report 3 - Bugs and Commands

## Part 1 - Bugs

### Failure-Inducing Input

Here is the JUnit test that induces a failure due to the buggy `reversed` method:

```java
@Test
public void testReversedFailure() {
  int[] input = {1, 2, 3, 4};
  int[] expected = {4, 3, 2, 1};
  assertArrayEquals(expected, ArrayExamples.reversed(input));
}
```
![image](https://raw.githubusercontent.com/zmc0806/cse15L-lab-report3/main/test1.jpeg)

This picture shows that after I add a test inducing fail,run 3 and fail 1.

### Input That Doesn't Induce Failure

Here is the JUnit test that does not induce a failure:

```java
@Test
public void testReversedNoFailure() {
  int[] input = {5};
  int[] expected = {5};
  assertArrayEquals(expected, ArrayExamples.reversed(input));
}
```
Such an array, when reversed, should look the same as the original. However, this test won't expose the bug in the reversed method (assuming the bug is related to handling arrays with more than one element).

![image](https://raw.githubusercontent.com/zmc0806/cse15L-lab-report3/main/test2.jpeg)

This picture shows I add again another test that does not induce a failure.So total run 4 test,and fail 1.

### Symptom

The symptom of the failure would be a failed JUnit test indicating that the expected reversed array does not match the actual array returned by the `reversed` method. (Note: A screenshot of the test results cannot be provided here, but would typically be included in this section of the report.)

### The Bug

Here is the buggy version of the `reversed` method:

```java
// BUGGY
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```

And here is the corrected version of the `reversed` method:

```java
// FIXED
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[i] = arr[arr.length - i - 1];
  }
  return newArray;
}
```

The fix addresses the issue by correctly creating a new reversed array and returning it, rather than incorrectly attempting to modify the original array.

## Part 2 - Researching Commands

### The `grep` Command

#### Option 1: `-i` (Ignore case)

```bash
grep -i "background" ./technical/biomed/
grep: ./technical/biomed/: Is a directory

Background
```
Function: Attempts to search for the word "background" in the specified directory.

Utility: This example is not useful as  `grep` does not search directories without additional options.

It's not useful for directory.

```bash
grep -i "example" ./technical/biomed/rr167.txt

        attributed to several factors. For example, an increase in
        could modify binding to the cell surface. For example,
```
Function: Searches for the word "example" in the file `rr167.txt`, ignoring case.

Utility: Useful for finding occurrences of a word regardless of its capitalization.


#### Option 2: `-r` (Recursive search)

```bash
grep -r "pattern" ./technical/
```
Function: Recursively searches for "pattern" in all files under the ./technical directory.

Utility: Beneficial for searching through a hierarchy of directories and files.


```bash
grep -r "era" ./technical/biomed/gb-2003-4-9-r60.txt
```
Function: Searches for "era" in the file `gb-2003-4-9-r60.txt`.

Utility: The `-r` option is redundant for a single file and is generally used for searching through multiple files.

#### Option 3: `-v` (Invert match)

```bash
grep -v "background" ./technical/biomed/
grep: ./technical/biomed/: Is a directory
```

Function: Attempts to filter out lines containing "background" in the specified directory.

Utility: Not useful since `grep` does not operate on directories without additional options.

```bash
grep -v "era" ./technical/biomed/gb-2003-4-9-r60.txt
```

Function: Excludes lines that contain the word "era" from the file `gb-2003-4-9-r60.txt`.

Utility: Useful for removing specific information or filtering out unwanted data.

#### Option 4: `-c` (Count)

```bash
grep -c "example" technical
grep: technical: Is a directory
```

Function: Attempts to count occurrences of "example" in the `technical` directory.

Utility: Not useful since `grep` cannot count occurrences in a directory without additional options.

```bash

grep -c "era" technical/biomed/gb-2003-4-9-r60.txt
35
```

Function: Counts the occurrences of "era" in the file `gb-2003-4-9-r60.txt`.

Utility: Helpful for quantitative analysis, such as counting keyword instances.

### Sources

The information for the `grep` command options was obtained from the manual pages (`man grep`) and various online resources. 

[man7.org Linux grep manual page](https://man7.org/linux/man-pages/man1/grep.1.html)


