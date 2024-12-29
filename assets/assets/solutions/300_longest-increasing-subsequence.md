# Longest Increasing Subsequence

## Problem Statement

Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

## Input

```text
nums = [10, 9, 2, 5, 3, 7, 101, 18]
```

## Output

```text
4
```

## Solutions

### Dart

```dart
int lengthOfLIS(List<int> nums) {
  List<int> dp = List.filled(nums.length, 1);
  int maxLen = 1;

  for (int i = 1; i < nums.length; i++) {
    for (int j = 0; j < i; j++) {
      if (nums[i] > nums[j]) {
        dp[i] = dp[i].clamp(dp[i], dp[j] + 1);
        maxLen = maxLen > dp[i] ? maxLen : dp[i];
      }
    }
  }
  return maxLen;
}
```

### C#

```csharp
public class Solution {
    public int LengthOfLIS(int[] nums) {
        int[] dp = new int[nums.Length];
        Array.Fill(dp, 1);
        int maxLen = 1;

        for (int i = 1; i < nums.Length; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.Max(dp[i], dp[j] + 1);
                    maxLen = Math.Max(maxLen, dp[i]);
                }
            }
        }
        return maxLen;
    }
}
```

### Java

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] dp = new int[nums.length];
        Arrays.fill(dp, 1);
        int maxLen = 1;

        for (int i = 1; i < nums.length; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                    maxLen = Math.max(maxLen, dp[i]);
                }
            }
        }
        return maxLen;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun lengthOfLIS(nums: IntArray): Int {
        val dp = IntArray(nums.size) { 1 }
        var maxLen = 1
        for (i in 1 until nums.size) {
            for (j in 0 until i) {
                if (nums[i] > nums[j]) {
                    dp[i] = maxOf(dp[i], dp[j] + 1)
                    maxLen = maxOf(maxLen, dp[i])
                }
            }
        }
        return maxLen
    }
}
```

### Swift

```swift
class Solution {
    func lengthOfLIS(_ nums: [Int]) -> Int {
        var dp = [Int](repeating: 1, count: nums.count)
        var maxLen = 1

        for i in 1..<nums.count {
            for j in 0..<i {
                if nums[i] > nums[j] {
                    dp[i] = max(dp[i], dp[j] + 1)
                    maxLen = max(maxLen, dp[i])
                }
            }
        }
        return maxLen
    }
}
```


### The End

