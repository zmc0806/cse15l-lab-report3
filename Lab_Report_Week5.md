# Lab Report 3 - Bugs and Commands (Week 5)

## Part 1 - Bugs

### Failure-Inducing Input

Here is the JUnit test that induces a failure due to the buggy `reversed` method:

\```java
@Test
public void testReversedFailure() {
  int[] input = {1, 2, 3, 4};
  int[] expected = {4, 3, 2, 1};
  assertArrayEquals(expected, ArrayExamples.reversed(input));
}
\```

### Input That Doesn't Induce Failure

Here is the JUnit test that does not induce a failure:

\```java
@Test
public void testReversedNoFailure() {
  int[] input = {};
  int[] expected = {};
  assertArrayEquals(expected, ArrayExamples.reversed(input));
}
\```

### Symptom

The symptom of the failure would be a failed JUnit test indicating that the expected reversed array does not match the actual array returned by the `reversed` method. (Note: A screenshot of the test results cannot be provided here, but would typically be included in this section of the report.)

### The Bug

Here is the buggy version of the `reversed` method:

\```java
// BUGGY
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
\```

And here is the corrected version of the `reversed` method:

\```java
// FIXED
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[i] = arr[arr.length - i - 1];
  }
  return newArray;
}
\```

The fix addresses the issue by correctly creating a new reversed array and returning it, rather than incorrectly attempting to modify the original array.

## Part 2 - Researching Commands

### The `grep` Command

#### Option 1: `-i` (Ignore case)

\```bash
grep -i "pattern" ./technical/file.txt
\```

This command will search for "pattern" in `file.txt` ignoring the case sensitivity. It's useful when the case of the text is unknown or mixed.

\```bash
grep -i "example" ./technical/documentation.md
\```

Searches for the word "example" in `documentation.md` without considering case.

#### Option 2: `-r` (Recursive search)

\```bash
grep -r "pattern" ./technical/
\```

Recursively search for "pattern" in all files under the `./technical` directory.

\```bash
grep -r "config" ./technical/config/
\```

Searches all files in the `./technical/config/` directory for the string "config".

#### Option 3: `-v` (Invert match)

\```bash
grep -v "pattern" ./technical/logs.txt
\```

This command will print all lines that do not contain the "pattern" in `logs.txt`. It's useful for filtering out unwanted lines.

\```bash
grep -v "error" ./technical/error_logs.txt
\```

Filters out lines that contain the word "error" in `error_logs.txt`.

#### Option 4: `-c` (Count)

\```bash
grep -c "pattern" ./technical/report.txt
\```

Counts the number of times "pattern" appears in `report.txt`.

\```bash
grep -c "TODO" ./technical/tasks.md
\```

Counts how many times "TODO" appears in `tasks.md`, which can be useful for tracking tasks.

### Sources

The information for the `grep` command options was obtained from the manual pages (`man grep`) and various online resources. Specific URLs are not provided, but a web search for "grep command-line options" will yield comprehensive guides and examples.

