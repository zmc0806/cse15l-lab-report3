# Lab Report 3 - Bugs and Commands (Week 5)

## Part 1 - Bugs

### Chosen Bug: Array Index Out of Bounds

#### Failure-Inducing Input

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class ArrayTest {
    
    @Test(expected = IndexOutOfBoundsException.class)
    public void testArrayIndexOutOfBounds() {
        int[] testArray = {1, 2, 3};
        int index = 3; // This is out of bounds since array indexes start at 0
        int value = testArray[index]; // This should throw IndexOutOfBoundsException
    }
}
