# Uncrossed Lines

## Problem Statement

You are given two integer arrays `nums1` and `nums2`. We can draw a connecting line between two numbers `nums1[i]` and `nums2[j]` if `nums1[i] == nums2[j]` and the line does not intersect any other connecting lines.

Return the maximum number of connecting lines we can draw in this way.

## Input

```text
nums1 = [1,4,2]
nums2 = [1,2,4]
```

## Output

```text
2
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxUncrossedLines(nums1: IntArray, nums2: IntArray): Int {
        val dp = Array(nums1.size + 1) { IntArray(nums2.size + 1) }

        for (i in 1..nums1.size) {
            for (j in 1..nums2.size) {
                if (nums1[i - 1] == nums2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1
                } else {
                    dp[i][j] = maxOf(dp[i - 1][j], dp[i][j - 1])
                }
            }
        }

        return dp[nums1.size][nums2.size]
    }
}
```

### Dart

```dart
int maxUncrossedLines(List<int> nums1, List<int> nums2) {
  List<List<int>> dp = List.generate(nums1.length + 1, (_) => List.filled(nums2.length + 1, 0));

  for (int i = 1; i <= nums1.length; i++) {
    for (int j = 1; j <= nums2.length; j++) {
      if (nums1[i - 1] == nums2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + 1;
      } else {
        dp[i][j] = dp[i - 1][j] > dp[i][j - 1] ? dp[i - 1][j] : dp[i][j - 1];
      }
    }
  }

  return dp[nums1.length][nums2.length];
}
```

### C#

```csharp
public class Solution {
    public int MaxUncrossedLines(int[] nums1, int[] nums2) {
        int[,] dp = new int[nums1.Length + 1, nums2.Length + 1];

        for (int i = 1; i <= nums1.Length; i++) {
            for (int j = 1; j <= nums2.Length; j++) {
                if (nums1[i - 1] == nums2[j - 1]) {
                    dp[i, j] = dp[i - 1, j - 1] + 1;
                } else {
                    dp[i, j] = Math.Max(dp[i - 1, j], dp[i, j - 1]);
                }
            }
        }

        return dp[nums1.Length, nums2.Length];
    }
}
```

### Java

```java
class Solution {
    public int maxUncrossedLines(int[] nums1, int[] nums2) {
        int[][] dp = new int[nums1.length + 1][nums2.length + 1];

        for (int i = 1; i <= nums1.length; i++) {
            for (int j = 1; j <= nums2.length; j++) {
                if (nums1[i - 1] == nums2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        return dp[nums1.length][nums2.length];
    }
}
```

### Swift

```swift
class Solution {
    func maxUncrossedLines(_ nums1: [Int], _ nums2: [Int]) -> Int {
        var dp = Array(repeating: Array(repeating: 0, count: nums2.count + 1), count: nums1.count + 1)

        for i in 1...nums1.count {
            for j in 1...nums2.count {
                if nums1[i - 1] == nums2[j - 1] {
                    dp[i][j] = dp[i - 1][j - 1] + 1
                } else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
                }
            }
        }

        return dp[nums1.count][nums2.count]
    }
}
```

### The End