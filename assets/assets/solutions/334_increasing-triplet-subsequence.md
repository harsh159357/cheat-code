# Increasing Triplet Subsequence

## Problem Statement

Given an integer array `nums`, return `true` if there exists a triple of indices \((i, j, k)\) such that \(i < j < k\) and \(nums[i] < nums[j] < nums[k]\). If no such indices exist, return `false`.

## Input

```text
nums = [1, 2, 3, 4, 5]
```

## Output

```text
true
```

## Input

```text
nums = [5, 4, 3, 2, 1]
```

## Output

```text
false
```

## Solutions

### Dart

```dart
bool increasingTriplet(List<int> nums) {
  int min1 = double.infinity.toInt();
  int min2 = double.infinity.toInt();
  for (int num in nums) {
    if (num <= min1) {
      min1 = num;
    } else if (num <= min2) {
      min2 = num;
    } else {
      return true;
    }
  }
  return false;
}
```

### C#

```csharp
public class Solution {
    public bool IncreasingTriplet(int[] nums) {
        int min1 = int.MaxValue;
        int min2 = int.MaxValue;
        foreach (var num in nums) {
            if (num <= min1) {
                min1 = num;
            } else if (num <= min2) {
                min2 = num;
            } else {
                return true;
            }
        }
        return false;
    }
}
```

### Java

```java
class Solution {
    public boolean increasingTriplet(int[] nums) {
        int min1 = Integer.MAX_VALUE, min2 = Integer.MAX_VALUE;
        for (int num : nums) {
            if (num <= min1) {
                min1 = num;
            } else if (num <= min2) {
                min2 = num;
            } else {
                return true;
            }
        }
        return false;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun increasingTriplet(nums: IntArray): Boolean {
        var min1 = Int.MAX_VALUE
        var min2 = Int.MAX_VALUE
        for (num in nums) {
            when {
                num <= min1 -> min1 = num
                num <= min2 -> min2 = num
                else -> return true
            }
        }
        return false
    }
}
```

### Swift

```swift
class Solution {
    func increasingTriplet(_ nums: [Int]) -> Bool {
        var min1 = Int.max
        var min2 = Int.max
        for num in nums {
            if num <= min1 {
                min1 = num
            } else if num <= min2 {
                min2 = num
            } else {
                return true
            }
        }
        return false
    }
}
```


### The End

