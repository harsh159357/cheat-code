# Longest Arithmetic Subsequence of Given Difference

## Problem Statement

Given an integer array `arr` and an integer `difference`, return the length of the longest subsequence in `arr` such that the difference between consecutive elements is equal to `difference`.

## Input

```text
arr = [1,5,7,8,5,3,4,2,1]
difference = 1
```

## Output

```text
4
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun longestSubsequence(arr: IntArray, difference: Int): Int {
        val dp = mutableMapOf<Int, Int>()
        var maxLen = 0

        for (num in arr) {
            val prevLen = dp.getOrDefault(num - difference, 0) + 1
            dp[num] = prevLen
            maxLen = maxOf(maxLen, prevLen)
        }

        return maxLen
    }
}
```

### Dart

```dart
int longestSubsequence(List<int> arr, int difference) {
  Map<int, int> dp = {};
  int maxLen = 0;

  for (int num in arr) {
    int prevLen = (dp[num - difference] ?? 0) + 1;
    dp[num] = prevLen;
    maxLen = maxLen > prevLen ? maxLen : prevLen;
  }

  return maxLen;
}
```

### C#

```csharp
public class Solution {
    public int LongestSubsequence(int[] arr, int difference) {
        Dictionary<int, int> dp = new Dictionary<int, int>();
        int maxLen = 0;

        foreach (int num in arr) {
            int prevLen = dp.ContainsKey(num - difference) ? dp[num - difference] + 1 : 1;
            dp[num] = prevLen;
            maxLen = Math.Max(maxLen, prevLen);
        }

        return maxLen;
    }
}
```

### Java

```java
class Solution {
    public int longestSubsequence(int[] arr, int difference) {
        Map<Integer, Integer> dp = new HashMap<>();
        int maxLen = 0;

        for (int num : arr) {
            int prevLen = dp.getOrDefault(num - difference, 0) + 1;
            dp.put(num, prevLen);
            maxLen = Math.max(maxLen, prevLen);
        }

        return maxLen;
    }
}
```

### Swift

```swift
class Solution {
    func longestSubsequence(_ arr: [Int], _ difference: Int) -> Int {
        var dp = [Int: Int]()
        var maxLen = 0

        for num in arr {
            let prevLen = (dp[num - difference] ?? 0) + 1
            dp[num] = prevLen
            maxLen = max(maxLen, prevLen)
        }

        return maxLen
    }
}
```

### The End