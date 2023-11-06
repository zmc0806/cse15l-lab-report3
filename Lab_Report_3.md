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
  int[] input = {1,2,3,4};
  int[] expected = {1,2,3,4};
  assertArrayEquals(expected, ArrayExamples.reversed(input));
}
```
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

It's not useful for directory.

```bash
grep -i "example" ./technical/biomed/rr167.txt

        attributed to several factors. For example, an increase in
        could modify binding to the cell surface. For example,
```

Searches for the word "example" in `rr167.txt` without considering case.

#### Option 2: `-r` (Recursive search)

```bash
grep -r "pattern" ./technical/
```

Recursively search for "pattern" in all files under the `./technical` directory.

```bash
grep -r "era" ./technical/biomed/gb-2003-4-9-r60.txt
```

Searches all word in the `gb-2003-4-9-r60.txt` file for the string contains "era".

#### Option 3: `-v` (Invert match)

```bash
grep -v "background" ./technical/biomed/
grep: ./technical/biomed/: Is a directory
```

It's not useful for directory.

```bash
grep -v "era" ./technical/biomed/gb-2003-4-9-r60.txt
```

Filters out lines that contain the word "era" in `gb-2003-4-9-r60.txt`.

#### Option 4: `-c` (Count)

```bash
grep -c "example" technical
grep: technical: Is a directory
```

It's not useful for directory.

```bash

grep -c "era" technical/biomed/gb-2003-4-9-r60.txt
35
```

Counts how many times "era" appears in `gb-2003-4-9-r60.txt`, which can be useful for tracking tasks.

### Sources

The information for the `grep` command options was obtained from the manual pages (`man grep`) and various online resources. 

https://man7.org/linux/man-pages/man1/grep.1.html

