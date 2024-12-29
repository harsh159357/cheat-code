# Find the Difference of Two Arrays

## Problem Statement

You are given two integer arrays `nums1` and `nums2`. Return a list of two lists:
1. The first list contains elements present in `nums1` but not in `nums2`.
2. The second list contains elements present in `nums2` but not in `nums1`.

Each list in the result should not have duplicate elements.

---

## Input

```text
nums1 = [1, 2, 3]
nums2 = [2, 4, 6]
```

## Output

```text
[[1, 3], [4, 6]]
```

---

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findDifference(nums1: IntArray, nums2: IntArray): List<List<Int>> {
        val set1 = nums1.toSet()
        val set2 = nums2.toSet()
        val result = mutableListOf<List<Int>>()

        val diff1 = set1.subtract(set2).toList()
        val diff2 = set2.subtract(set1).toList()

        result.add(diff1)
        result.add(diff2)

        return result
    }
}

fun main() {
    val solution = Solution()
    val nums1 = intArrayOf(1, 2, 3)
    val nums2 = intArrayOf(2, 4, 6)
    println(solution.findDifference(nums1, nums2)) // Output: [[1, 3], [4, 6]]
}
```


### Dart

```dart
List<List<int>> findDifference(List<int> nums1, List<int> nums2) {
  final set1 = nums1.toSet();
  final set2 = nums2.toSet();

  final diff1 = set1.difference(set2).toList();
  final diff2 = set2.difference(set1).toList();

  return [diff1, diff2];
}

void main() {
  print(findDifference([1, 2, 3], [2, 4, 6])); // Output: [[1, 3], [4, 6]]
}
```


### C#

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Solution {
    public IList<IList<int>> FindDifference(int[] nums1, int[] nums2) {
        var set1 = new HashSet<int>(nums1);
        var set2 = new HashSet<int>(nums2);

        var diff1 = set1.Except(set2).ToList();
        var diff2 = set2.Except(set1).ToList();

        return new List<IList<int>> { diff1, diff2 };
    }
}

class Program {
    static void Main() {
        var solution = new Solution();
        var nums1 = new[] { 1, 2, 3 };
        var nums2 = new[] { 2, 4, 6 };
        var result = solution.FindDifference(nums1, nums2);
        Console.WriteLine($"[{string.Join(", ", result[0])}], [{string.Join(", ", result[1])}]");
    }
}
```


### Java

```java
import java.util.*;

class Solution {
    public List<List<Integer>> findDifference(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        Set<Integer> set2 = new HashSet<>();
        
        for (int num : nums1) {
            set1.add(num);
        }
        for (int num : nums2) {
            set2.add(num);
        }
        
        List<Integer> diff1 = new ArrayList<>(set1);
        diff1.removeAll(set2);
        List<Integer> diff2 = new ArrayList<>(set2);
        diff2.removeAll(set1);
        
        return Arrays.asList(diff1, diff2);
    }
}
```


### Swift

```swift
class Solution {
    func findDifference(_ nums1: [Int], _ nums2: [Int]) -> [[Int]] {
        let set1 = Set(nums1)
        let set2 = Set(nums2)

        let diff1 = Array(set1.subtracting(set2))
        let diff2 = Array(set2.subtracting(set1))

        return [diff1, diff2]
    }
}

let solution = Solution()
let nums1 = [1, 2, 3]
let nums2 = [2, 4, 6]
print(solution.findDifference(nums1, nums2)) // Output: [[1, 3], [4, 6]]
```

### The End