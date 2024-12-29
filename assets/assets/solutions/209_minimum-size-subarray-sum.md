# Minimum Size Subarray Sum

## Problem Statement

Given an array of positive integers `nums` and a positive integer `target`, return the minimal length of a contiguous subarray of which the sum is greater than or equal to `target`. If there is no such subarray, return `0`.

## Input

```text
target = 7
nums = [2, 3, 1, 2, 4, 3]
```

## Output

```text
2
```

## Solutions

### Dart

```dart
int minSubArrayLen(int target, List<int> nums) {
  int minLength = nums.length + 1;
  int sum = 0;
  int left = 0;

  for (int right = 0; right < nums.length; right++) {
    sum += nums[right];

    while (sum >= target) {
      minLength = (right - left + 1 < minLength) ? right - left + 1 : minLength;
      sum -= nums[left];
      left++;
    }
  }

  return minLength == nums.length + 1 ? 0 : minLength;
}
```

### C#

```csharp
public class Solution {
    public int MinSubArrayLen(int target, int[] nums) {
        int minLength = int.MaxValue;
        int sum = 0, left = 0;

        for (int right = 0; right < nums.Length; right++) {
            sum += nums[right];

            while (sum >= target) {
                minLength = Math.Min(minLength, right - left + 1);
                sum -= nums[left++];
            }
        }

        return minLength == int.MaxValue ? 0 : minLength;
    }
}
```

### Java

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int minLength = Integer.MAX_VALUE;
        int sum = 0;
        int left = 0;

        for (int right = 0; right < nums.length; right++) {
            sum += nums[right];

            while (sum >= target) {
                minLength = Math.min(minLength, right - left + 1);
                sum -= nums[left++];
            }
        }

        return minLength == Integer.MAX_VALUE ? 0 : minLength;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun minSubArrayLen(target: Int, nums: IntArray): Int {
        var minLength = Int.MAX_VALUE
        var sum = 0
        var left = 0

        for (right in nums.indices) {
            sum += nums[right]

            while (sum >= target) {
                minLength = minOf(minLength, right - left + 1)
                sum -= nums[left]
                left++
            }
        }

        return if (minLength == Int.MAX_VALUE) 0 else minLength
    }
}
```

### Swift

```swift
class Solution {
    func minSubArrayLen(_ target: Int, _ nums: [Int]) -> Int {
        var minLength = Int.max
        var sum = 0
        var left = 0

        for right in 0..<nums.count {
            sum += nums[right]

            while sum >= target {
                minLength = min(minLength, right - left + 1)
                sum -= nums[left]
                left += 1
            }
        }

        return minLength == Int.max ? 0 : minLength
    }
}
```

### The End

