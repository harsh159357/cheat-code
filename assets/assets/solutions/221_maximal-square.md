# Maximal Square

## Problem Statement

Given an `m x n` binary matrix filled with `'0'`s and `'1'`s, find the largest square containing only `'1'`s and return its area.

## Input

```text
matrix = [
    ['1', '0', '1', '0', '0'],
    ['1', '0', '1', '1', '1'],
    ['1', '1', '1', '1', '1'],
    ['1', '0', '0', '1', '0']
]
```

## Output

```text
4
```

## Solutions

### Dart

```dart
int maximalSquare(List<List<String>> matrix) {
  if (matrix.isEmpty) return 0;
  int m = matrix.length;
  int n = matrix[0].length;
  List<List<int>> dp = List.generate(m + 1, (_) => List.filled(n + 1, 0));
  int maxLen = 0;

  for (int i = 1; i <= m; i++) {
    for (int j = 1; j <= n; j++) {
      if (matrix[i - 1][j - 1] == '1') {
        dp[i][j] = 1 + [
          dp[i - 1][j - 1],
          dp[i - 1][j],
          dp[i][j - 1]
        ].reduce((a, b) => a < b ? a : b);
        maxLen = maxLen > dp[i][j] ? maxLen : dp[i][j];
      }
    }
  }

  return maxLen * maxLen;
}
```

### C#

```csharp
public class Solution {
    public int MaximalSquare(char[][] matrix) {
        if (matrix.Length == 0) return 0;
        int m = matrix.Length, n = matrix[0].Length, maxLen = 0;
        int[,] dp = new int[m + 1, n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (matrix[i - 1][j - 1] == '1') {
                    dp[i, j] = 1 + Math.Min(dp[i - 1, j - 1], Math.Min(dp[i - 1, j], dp[i, j - 1]));
                    maxLen = Math.Max(maxLen, dp[i, j]);
                }
            }
        }

        return maxLen * maxLen;
    }
}
```

### Java

```java
class Solution {
    public int maximalSquare(char[][] matrix) {
        if (matrix.length == 0) return 0;
        int m = matrix.length, n = matrix[0].length, maxLen = 0;
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (matrix[i - 1][j - 1] == '1') {
                    dp[i][j] = 1 + Math.min(dp[i - 1][j - 1], Math.min(dp[i - 1][j], dp[i][j - 1]));
                    maxLen = Math.max(maxLen, dp[i][j]);
                }
            }
        }

        return maxLen * maxLen;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun maximalSquare(matrix: Array<CharArray>): Int {
        if (matrix.isEmpty()) return 0
        val m = matrix.size
        val n = matrix[0].size
        val dp = Array(m + 1) { IntArray(n + 1) }
        var maxLen = 0
        for (i in 1..m) {
            for (j in 1..n) {
                if (matrix[i - 1][j - 1] == '1') {
                    dp[i][j] = 1 + minOf(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1])
                    maxLen = maxOf(maxLen, dp[i][j])
                }
            }
        }
        return maxLen * maxLen
    }
}
```

### Swift

```swift
class Solution {
    func maximalSquare(_ matrix: [[Character]]) -> Int {
        if matrix.isEmpty { return 0 }
        let m = matrix.count, n = matrix[0].count
        var dp = Array(repeating: Array(repeating: 0, count: n + 1), count: m + 1)
        var maxLen = 0

        for i in 1...m {
            for j in 1...n {
                if matrix[i - 1][j - 1] == "1" {
                    dp[i][j] = 1 + min(dp[i - 1][j - 1], min(dp[i - 1][j], dp[i][j - 1]))
                    maxLen = max(maxLen, dp[i][j])
                }
            }
        }

        return maxLen * maxLen
    }
}
```


### The End

