# Number of Longest Increasing Subsequence

## Problem Statement

Given an integer array `nums`, return the number of longest increasing subsequences.

A subsequence is a sequence derived from an array by deleting some or no elements without changing the order of the remaining elements. A subsequence is increasing if each element is strictly smaller than its successor.

## Input

```text
nums = [1, 3, 5, 4, 7]
```

## Output

```text
2
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun findNumberOfLIS(nums: IntArray): Int {
        val n = nums.size
        val dp = Array(n) { Pair(1, 1) } // (length of LIS ending here, count of LIS ending here)
        var max = 1

        for (right in 0 until n) {
            for (left in 0 until right) {
                if (nums[left] < nums[right]) {
                    if (dp[left].first + 1 > dp[right].first) {
                        dp[right] = Pair(dp[left].first + 1, dp[left].second)
                        max = Math.max(max, dp[right].first)
                    } else if (dp[left].first + 1 == dp[right].first) {
                        dp[right] = Pair(dp[right].first, dp[right].second + dp[left].second)
                    }
                }
            }
        }

        var result = 0
        for (pair in dp) {
            if (pair.first == max) {
                result += pair.second
            }
        }

        return result
    }
}

fun main() {
    val nums = intArrayOf(1, 3, 5, 4, 7)
    val solution = Solution()
    println("Number of longest increasing subsequences: ${solution.findNumberOfLIS(nums)}") // Output: 2
}
```


### Dart

```dart
int findNumberOfLIS(List<int> nums) {
  int n = nums.length;
  List<List<int>> dp = List.generate(n, (_) => [1, 1]);
  int maxLength = 1;

  for (int right = 0; right < n; right++) {
    for (int left = 0; left < right; left++) {
      if (nums[left] < nums[right]) {
        if (dp[left][0] + 1 > dp[right][0]) {
          dp[right] = [dp[left][0] + 1, dp[left][1]];
          maxLength = maxLength > dp[right][0] ? maxLength : dp[right][0];
        } else if (dp[left][0] + 1 == dp[right][0]) {
          dp[right][1] += dp[left][1];
        }
      }
    }
  }

  int result = 0;
  for (var pair in dp) {
    if (pair[0] == maxLength) {
      result += pair[1];
    }
  }

  return result;
}

void main() {
  List<int> nums = [1, 3, 5, 4, 7];
  print("Number of longest increasing subsequences: ${findNumberOfLIS(nums)}"); // Output: 2
}
```


### C#

```csharp
public class Solution {
    public int FindNumberOfLIS(int[] nums) {
        int n = nums.Length;
        var dp = new (int Length, int Count)[n];
        for (int i = 0; i < n; i++) dp[i] = (1, 1);
        int max = 1;

        for (int right = 0; right < n; right++) {
            for (int left = 0; left < right; left++) {
                if (nums[left] < nums[right]) {
                    if (dp[left].Length + 1 > dp[right].Length) {
                        dp[right] = (dp[left].Length + 1, dp[left].Count);
                        max = Math.Max(max, dp[right].Length);
                    } else if (dp[left].Length + 1 == dp[right].Length) {
                        dp[right].Count += dp[left].Count;
                    }
                }
            }
        }

        int result = 0;
        foreach (var pair in dp) {
            if (pair.Length == max) result += pair.Count;
        }
        return result;
    }
}
```


### Java

```java
class Solution {
    public int findNumberOfLIS(int[] nums) {
        int n = nums.length;
        int[][] dp = new int[n][2]; // dp[i][0]: length of LIS ending at i, dp[i][1]: count of LIS ending at i
        for (int i = 0; i < n; i++) {
            dp[i][0] = 1;
            dp[i][1] = 1;
        }
        int max = 1;

        for (int right = 0; right < n; right++) {
            for (int left = 0; left < right; left++) {
                if (nums[left] < nums[right]) {
                    if (dp[left][0] + 1 > dp[right][0]) {
                        dp[right][0] = dp[left][0] + 1;
                        dp[right][1] = dp[left][1];
                        max = Math.max(max, dp[right][0]);
                    } else if (dp[left][0] + 1 == dp[right][0]) {
                        dp[right][1] += dp[left][1];
                    }
                }
            }
        }

        int result = 0;
        for (int[] pair : dp) {
            if (pair[0] == max) {
                result += pair[1];
            }
        }

        return result;
    }
}
```


### Swift

```swift
class Solution {
    func findNumberOfLIS(_ nums: [Int]) -> Int {
        let n = nums.count
        var dp = Array(repeating: (length: 1, count: 1), count: n)
        var maxLength = 1

        for right in 0..<n {
            for left in 0..<right {
                if nums[left] < nums[right] {
                    if dp[left].length + 1 > dp[right].length {
                        dp[right] = (dp[left].length + 1, dp[left].count)
                        maxLength = max(maxLength, dp[right].length)
                    } else if dp[left].length + 1 == dp[right].length {
                        dp[right].count += dp[left].count
                    }
                }
            }
        }

        return dp.filter { $0.length == maxLength }.reduce(0) { $0 + $1.count }
    }
}

// Example usage
let nums = [1, 3, 5, 4, 7]
let solution = Solution()
print("Number of longest increasing subsequences: \(solution.findNumberOfLIS(nums))") // Output: 2
```

### The End