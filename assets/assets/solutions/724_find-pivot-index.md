# Find Pivot Index

## Problem Statement

Given an array of integers `nums`, calculate the pivot index of this array.

The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right.

If no such index exists, return -1. If there are multiple pivot indexes, return the left-most pivot index.

## Input

```text
nums = [1, 7, 3, 6, 5, 6]
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int pivotIndex(List<int> nums) {
  int totalSum = nums.reduce((a, b) => a + b);
  int leftSum = 0;

  for (int i = 0; i < nums.length; i++) {
    if (leftSum == totalSum - leftSum - nums[i]) {
      return i;
    }
    leftSum += nums[i];
  }
  return -1;
}
```

### C#

```csharp
public class Solution {
    public int PivotIndex(int[] nums) {
        int totalSum = 0, leftSum = 0;

        foreach (int num in nums) {
            totalSum += num;
        }

        for (int i = 0; i < nums.Length; i++) {
            if (leftSum == totalSum - leftSum - nums[i]) {
                return i;
            }
            leftSum += nums[i];
        }

        return -1;
    }
}
```

### Java

```java
class Solution {
    public int pivotIndex(int[] nums) {
        int totalSum = 0, leftSum = 0;

        for (int num : nums) {
            totalSum += num;
        }

        for (int i = 0; i < nums.length; i++) {
            if (leftSum == totalSum - leftSum - nums[i]) {
                return i;
            }
            leftSum += nums[i];
        }

        return -1;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun pivotIndex(nums: IntArray): Int {
        val totalSum = nums.sum()
        var leftSum = 0

        for (i in nums.indices) {
            if (leftSum == totalSum - leftSum - nums[i]) {
                return i
            }
            leftSum += nums[i]
        }
        return -1
    }
}
```

### Swift

```swift
class Solution {
    func pivotIndex(_ nums: [Int]) -> Int {
        let totalSum = nums.reduce(0, +)
        var leftSum = 0

        for (i, num) in nums.enumerated() {
            if leftSum == totalSum - leftSum - num {
                return i
            }
            leftSum += num
        }
        return -1
    }
}
```


### The End