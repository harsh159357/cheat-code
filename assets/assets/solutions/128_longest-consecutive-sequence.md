# Longest Consecutive Sequence

## Problem Statement

Given an unsorted array of integers `nums`, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in `O(n)` time.

---

## Input

```text
nums = [100, 4, 200, 1, 3, 2]
```

## Output

```text
4
```


## Solutions

### Dart

```dart
int longestConsecutive(List<int> nums) {
  if (nums.isEmpty) return 0;

  final numSet = nums.toSet();
  int maxLength = 0;

  for (int num in numSet) {
    if (!numSet.contains(num - 1)) { // Start of a new sequence
      int currentNum = num;
      int currentLength = 1;

      while (numSet.contains(currentNum + 1)) {
        currentNum++;
        currentLength++;
      }

      maxLength = maxLength > currentLength ? maxLength : currentLength;
    }
  }

  return maxLength;
}
```


### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public int LongestConsecutive(int[] nums) {
        if (nums.Length == 0) return 0;

        var numSet = new HashSet<int>(nums);
        int maxLength = 0;

        foreach (int num in numSet) {
            if (!numSet.Contains(num - 1)) { // Start of a new sequence
                int currentNum = num;
                int currentLength = 1;

                while (numSet.Contains(currentNum + 1)) {
                    currentNum++;
                    currentLength++;
                }

                maxLength = Math.Max(maxLength, currentLength);
            }
        }

        return maxLength;
    }
}
```


### Java

```java
import java.util.HashSet;

class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums.length == 0) return 0;

        HashSet<Integer> numSet = new HashSet<>();
        for (int num : nums) {
            numSet.add(num);
        }

        int maxLength = 0;

        for (int num : numSet) {
            if (!numSet.contains(num - 1)) { // Start of a new sequence
                int currentNum = num;
                int currentLength = 1;

                while (numSet.contains(currentNum + 1)) {
                    currentNum++;
                    currentLength++;
                }

                maxLength = Math.max(maxLength, currentLength);
            }
        }

        return maxLength;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun longestConsecutive(nums: IntArray): Int {
        if (nums.isEmpty()) return 0

        val numSet = nums.toHashSet()
        var maxLength = 0

        for (num in numSet) {
            if (!numSet.contains(num - 1)) { // Start of a new sequence
                var currentNum = num
                var currentLength = 1

                while (numSet.contains(currentNum + 1)) {
                    currentNum++
                    currentLength++
                }

                maxLength = maxOf(maxLength, currentLength)
            }
        }

        return maxLength
    }
}
```


### Swift

```swift
class Solution {
    func longestConsecutive(_ nums: [Int]) -> Int {
        if nums.isEmpty { return 0 }

        let numSet = Set(nums)
        var maxLength = 0

        for num in numSet {
            if !numSet.contains(num - 1) { // Start of a new sequence
                var currentNum = num
                var currentLength = 1

                while numSet.contains(currentNum + 1) {
                    currentNum += 1
                    currentLength += 1
                }

                maxLength = max(maxLength, currentLength)
            }
        }

        return maxLength
    }
}
```

### The End

