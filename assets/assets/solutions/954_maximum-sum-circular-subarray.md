# Maximum Sum Circular Subarray

## Problem Statement

Given a circular integer array `nums` of length `n`, return the maximum possible sum of a non-empty subarray of `nums`.

A circular array means the end of the array connects to the beginning of the array. Formally, the next element of `nums[i]` is `nums[(i + 1) % n]` and the previous element of `nums[i]` is `nums[(i - 1 + n) % n]`.

## Input

```text
nums = [1, -2, 3, -2]
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxSubarraySumCircular(nums: IntArray): Int {
        var min = Int.MAX_VALUE
        var curMin = 0
        var max = Int.MIN_VALUE
        var curMax = 0
        var sum = 0

        nums.forEach { n ->
            curMin = minOf(curMin + n, n)
            min = minOf(min, curMin)
            curMax = maxOf(curMax + n, n)
            max = maxOf(max, curMax)
            sum += n
        }

        return if (max < 0) max else maxOf(max, sum - min)
    }
}
```

### Dart

```dart
int maxSubarraySumCircular(List<int> nums) {
  int min = nums[0], curMin = 0, max = nums[0], curMax = 0, sum = 0;

  for (int n in nums) {
    curMin = (curMin + n).clamp(n, double.infinity).toInt();
    min = curMin < min ? curMin : min;
    curMax = (curMax + n).clamp(n, double.infinity).toInt();
    max = curMax > max ? curMax : max;
    sum += n;
  }

  return max < 0 ? max : max > sum - min ? max : sum - min;
}
```

### C#

```csharp
public class Solution {
    public int MaxSubarraySumCircular(int[] nums) {
        int min = int.MaxValue, curMin = 0, max = int.MinValue, curMax = 0, sum = 0;

        foreach (int n in nums) {
            curMin = Math.Min(curMin + n, n);
            min = Math.Min(min, curMin);
            curMax = Math.Max(curMax + n, n);
            max = Math.Max(max, curMax);
            sum += n;
        }

        return max < 0 ? max : Math.Max(max, sum - min);
    }
}
```

### Java

```java
class Solution {
    public int maxSubarraySumCircular(int[] nums) {
        int min = Integer.MAX_VALUE, curMin = 0, max = Integer.MIN_VALUE, curMax = 0, sum = 0;

        for (int n : nums) {
            curMin = Math.min(curMin + n, n);
            min = Math.min(min, curMin);
            curMax = Math.max(curMax + n, n);
            max = Math.max(max, curMax);
            sum += n;
        }

        return max < 0 ? max : Math.max(max, sum - min);
    }
}
```

### Swift

```swift
class Solution {
    func maxSubarraySumCircular(_ nums: [Int]) -> Int {
        var min = Int.max, curMin = 0, max = Int.min, curMax = 0, sum = 0

        for n in nums {
            curMin = Swift.min(curMin + n, n)
            min = Swift.min(min, curMin)
            curMax = Swift.max(curMax + n, n)
            max = Swift.max(max, curMax)
            sum += n
        }

        return max < 0 ? max : Swift.max(max, sum - min)
    }
}
```

### The End