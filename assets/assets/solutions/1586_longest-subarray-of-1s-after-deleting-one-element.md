# Longest Subarray of 1's After Deleting One Element

## Problem Statement

Given a binary array `nums`, you can delete at most one element from the array. Return the length of the longest subarray containing only `1`s after deleting one element.

## Input

```text
nums = [1,1,0,1]
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun longestSubarray(nums: IntArray): Int {
        var left = 0
        var right = 0
        var zeroCount = 0
        var maxLen = 0

        while (right < nums.size) {
            if (nums[right] == 0) zeroCount++

            while (zeroCount > 1) {
                if (nums[left] == 0) zeroCount--
                left++
            }

            maxLen = maxOf(maxLen, right - left)
            right++
        }

        return maxLen
    }
}
```

### Dart

```dart
int longestSubarray(List<int> nums) {
  int left = 0, right = 0, zeroCount = 0, maxLen = 0;

  while (right < nums.length) {
    if (nums[right] == 0) zeroCount++;

    while (zeroCount > 1) {
      if (nums[left] == 0) zeroCount--;
      left++;
    }

    maxLen = max(maxLen, right - left);
    right++;
  }

  return maxLen;
}
```

### C#

```csharp
public class Solution {
    public int LongestSubarray(int[] nums) {
        int left = 0, right = 0, zeroCount = 0, maxLen = 0;

        while (right < nums.Length) {
            if (nums[right] == 0) zeroCount++;

            while (zeroCount > 1) {
                if (nums[left] == 0) zeroCount--;
                left++;
            }

            maxLen = Math.Max(maxLen, right - left);
            right++;
        }

        return maxLen;
    }
}
```

### Java

```java
class Solution {
    public int longestSubarray(int[] nums) {
        int left = 0, right = 0, zeroCount = 0, maxLen = 0;

        while (right < nums.length) {
            if (nums[right] == 0) zeroCount++;

            while (zeroCount > 1) {
                if (nums[left] == 0) zeroCount--;
                left++;
            }

            maxLen = Math.max(maxLen, right - left);
            right++;
        }

        return maxLen;
    }
}
```

### Swift

```swift
class Solution {
    func longestSubarray(_ nums: [Int]) -> Int {
        var left = 0, right = 0, zeroCount = 0, maxLen = 0

        while right < nums.count {
            if nums[right] == 0 { zeroCount += 1 }

            while zeroCount > 1 {
                if nums[left] == 0 { zeroCount -= 1 }
                left += 1
            }

            maxLen = max(maxLen, right - left)
            right += 1
        }

        return maxLen
    }
}
```

### The End