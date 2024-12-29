# Find the Duplicate Number

## Problem Statement

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, return the duplicate number.

**Note:**
- There is only one duplicate number in the array, but it could be repeated more than once.
- You must solve the problem without modifying the array and use constant extra space.

## Input

```text
nums = [1,3,4,2,2]
```

## Output

```text
2
```

## Solutions

### Dart

```dart
int findDuplicate(List<int> nums) {
  Set<int> seen = {};
  for (int num in nums) {
    if (seen.contains(num)) return num;
    seen.add(num);
  }
  return -1;
}
```

### C#

```csharp
public class Solution {
    public int FindDuplicate(int[] nums) {
        HashSet<int> seen = new HashSet<int>();
        foreach (int num in nums) {
            if (seen.Contains(num)) return num;
            seen.Add(num);
        }
        return -1;
    }
}
```

### Java

```java
class Solution {
    public int findDuplicate(int[] nums) {
        Set<Integer> seen = new HashSet<>();
        for (int num : nums) {
            if (seen.contains(num)) return num;
            seen.add(num);
        }
        return -1;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun findDuplicate(nums: IntArray): Int {
        val seen = mutableSetOf<Int>()
        for (num in nums) {
            if (num in seen) return num
            seen.add(num)
        }
        return -1
    }
}
```

### Swift

```swift
class Solution {
    func findDuplicate(_ nums: [Int]) -> Int {
        var seen = Set<Int>()
        for num in nums {
            if seen.contains(num) {
                return num
            }
            seen.insert(num)
        }
        return -1
    }
}
```

### The End

