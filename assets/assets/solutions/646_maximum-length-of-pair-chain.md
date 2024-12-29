# Maximum Length of Pair Chain

## Problem Statement

You are given an array of `n` pairs `pairs` where `pairs[i] = [a, b]` and `a < b`. A pair `[c, d]` can follow another pair `[a, b]` if and only if `b < c`. A chain of pairs can be formed in this fashion.

Return the length of the longest chain that can be formed.

## Input

```text
pairs = [[1, 2], [2, 3], [3, 4]]
```

## Output

```text
2
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findLongestChain(pairs: Array<IntArray>): Int {
        // Sort the pairs based on the second element of each pair
        pairs.sortBy { it[1] }

        // Initialize the count to keep track of the length of the chain
        var count = 0
        // Initialize the end value to keep track of the end of the current chain
        var end = Int.MIN_VALUE

        // Iterate through each pair
        for (pair in pairs) {
            // If the first element of the current pair is greater than the end value
            if (pair[0] > end) {
                count++
                end = pair[1]
            }
        }

        // Return the length of the longest chain
        return count
    }
}

fun main() {
    val pairs = arrayOf(intArrayOf(1, 2), intArrayOf(2, 3), intArrayOf(3, 4))
    val solution = Solution()
    println("Maximum length of pair chain: ${solution.findLongestChain(pairs)}") // Output: 2
}
```

---

### Dart

```dart
int findLongestChain(List<List<int>> pairs) {
  // Sort the pairs based on the second element of each pair
  pairs.sort((a, b) => a[1].compareTo(b[1]));

  int count = 0;
  int end = -1001; // Minimum value considering constraints

  for (var pair in pairs) {
    if (pair[0] > end) {
      count++;
      end = pair[1];
    }
  }

  return count;
}

void main() {
  List<List<int>> pairs = [[1, 2], [2, 3], [3, 4]];
  print("Maximum length of pair chain: ${findLongestChain(pairs)}"); // Output: 2
}
```

---

### C#

```csharp
public class Solution {
    public int FindLongestChain(int[][] pairs) {
        // Sort the pairs based on the second element of each pair
        Array.Sort(pairs, (a, b) => a[1].CompareTo(b[1]));

        int count = 0;
        int end = int.MinValue;

        foreach (var pair in pairs) {
            if (pair[0] > end) {
                count++;
                end = pair[1];
            }
        }

        return count;
    }
}
```

---

### Java

```java
import java.util.Arrays;

class Solution {
    public int findLongestChain(int[][] pairs) {
        // Sort the pairs based on the second element of each pair
        Arrays.sort(pairs, (a, b) -> Integer.compare(a[1], b[1]));

        int count = 0;
        int end = Integer.MIN_VALUE;

        for (int[] pair : pairs) {
            if (pair[0] > end) {
                count++;
                end = pair[1];
            }
        }

        return count;
    }
}
```

---

### Swift

```swift
class Solution {
    func findLongestChain(_ pairs: [[Int]]) -> Int {
        // Sort the pairs based on the second element of each pair
        let sortedPairs = pairs.sorted { $0[1] < $1[1] }

        var count = 0
        var end = Int.min

        for pair in sortedPairs {
            if pair[0] > end {
                count += 1
                end = pair[1]
            }
        }

        return count
    }
}

// Example usage
let pairs = [[1, 2], [2, 3], [3, 4]]
let solution = Solution()
print("Maximum length of pair chain: \(solution.findLongestChain(pairs))") // Output: 2
```

### The End