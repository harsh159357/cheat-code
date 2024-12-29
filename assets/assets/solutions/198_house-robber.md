# House Robber

## Problem Statement

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. The only constraint stopping you from robbing all of them is that adjacent houses have security systems connected, and it will automatically contact the police if two adjacent houses are broken into on the same night.

Given an integer array `nums` representing the amount of money of each house, return the maximum amount of money you can rob without alerting the police.

## Input

```text
nums = [2,7,9,3,1]
```

## Output

```text
12
```

## Solutions

### Dart

```dart
int rob(List<int> nums) {
  if (nums.isEmpty) return 0;
  if (nums.length == 1) return nums[0];
  int prev1 = nums[0];
  int prev2 = nums[0] > nums[1] ? nums[0] : nums[1];
  for (int i = 2; i < nums.length; i++) {
    int current = (prev1 + nums[i]) > prev2 ? (prev1 + nums[i]) : prev2;
    prev1 = prev2;
    prev2 = current;
  }
  return prev2;
}
```

### C#

```csharp
public class Solution {
    public int Rob(int[] nums) {
        if (nums.Length == 0) return 0;
        if (nums.Length == 1) return nums[0];
        int prev1 = nums[0];
        int prev2 = Math.Max(nums[0], nums[1]);
        for (int i = 2; i < nums.Length; i++) {
            int current = Math.Max(prev1 + nums[i], prev2);
            prev1 = prev2;
            prev2 = current;
        }
        return prev2;
    }
}
```

### Java

```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 0) return 0;
        if (nums.length == 1) return nums[0];
        int prev1 = nums[0];
        int prev2 = Math.max(nums[0], nums[1]);
        for (int i = 2; i < nums.length; i++) {
            int current = Math.max(prev1 + nums[i], prev2);
            prev1 = prev2;
            prev2 = current;
        }
        return prev2;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun rob(nums: IntArray): Int {
        if (nums.isEmpty()) return 0
        if (nums.size == 1) return nums[0]
        var prev1 = nums[0]
        var prev2 = maxOf(nums[0], nums[1])
        for (i in 2 until nums.size) {
            val current = maxOf(prev1 + nums[i], prev2)
            prev1 = prev2
            prev2 = current
        }
        return prev2
    }
}
```

### Swift

```swift
class Solution {
    func rob(_ nums: [Int]) -> Int {
        if nums.isEmpty { return 0 }
        if nums.count == 1 { return nums[0] }
        var prev1 = nums[0]
        var prev2 = max(nums[0], nums[1])
        for i in 2..<nums.count {
            let current = max(prev1 + nums[i], prev2)
            prev1 = prev2
            prev2 = current
        }
        return prev2
    }
}
```

### The End

