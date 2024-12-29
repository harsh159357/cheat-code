# Max Consecutive Ones III

## Problem Statement

Given a binary array `nums` and an integer `k`, return the maximum number of consecutive `1`s in the array if you can flip at most `k` `0`s to `1`s.

## Input

```text
nums = [1,1,1,0,0,0,1,1,1,1,0]
k = 2
```

## Output

```text
6
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun longestOnes(nums: IntArray, k: Int): Int {
        var maxCount = 0
        var left = 0
        var zeroCount = 0

        for (right in nums.indices) {
            if (nums[right] == 0) zeroCount++
            while (zeroCount > k) {
                if (nums[left] == 0) zeroCount--
                left++
            }
            maxCount = maxOf(maxCount, right - left + 1)
        }

        return maxCount
    }
}
```

### Dart

```dart
int longestOnes(List<int> nums, int k) {
  int maxCount = 0;
  int left = 0;
  int zeroCount = 0;

  for (int right = 0; right < nums.length; right++) {
    if (nums[right] == 0) zeroCount++;
    while (zeroCount > k) {
      if (nums[left] == 0) zeroCount--;
      left++;
    }
    maxCount = maxCount > (right - left + 1) ? maxCount : (right - left + 1);
  }

  return maxCount;
}
```

### C#

```csharp
public class Solution {
    public int LongestOnes(int[] nums, int k) {
        int maxCount = 0, left = 0, zeroCount = 0;

        for (int right = 0; right < nums.Length; right++) {
            if (nums[right] == 0) zeroCount++;
            while (zeroCount > k) {
                if (nums[left] == 0) zeroCount--;
                left++;
            }
            maxCount = Math.Max(maxCount, right - left + 1);
        }

        return maxCount;
    }
}
```

### Java

```java
class Solution {
    public int longestOnes(int[] nums, int k) {
        int maxCount = 0, left = 0, zeroCount = 0;

        for (int right = 0; right < nums.length; right++) {
            if (nums[right] == 0) zeroCount++;
            while (zeroCount > k) {
                if (nums[left] == 0) zeroCount--;
                left++;
            }
            maxCount = Math.max(maxCount, right - left + 1);
        }

        return maxCount;
    }
}
```

### Swift

```swift
class Solution {
    func longestOnes(_ nums: [Int], _ k: Int) -> Int {
        var maxCount = 0
        var left = 0
        var zeroCount = 0

        for right in 0..<nums.count {
            if nums[right] == 0 { zeroCount += 1 }
            while zeroCount > k {
                if nums[left] == 0 { zeroCount -= 1 }
                left += 1
            }
            maxCount = max(maxCount, right - left + 1)
        }

        return maxCount
    }
}
```

### The End