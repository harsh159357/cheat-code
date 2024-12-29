# Distinct Subsequences

## Problem Statement

Given two strings `s` and `t`, return the number of distinct subsequences of `s` that equal `t`.

A string's subsequence is a new string formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters.

## Input

```text
s = "rabbbit"
t = "rabbit"
```

## Output

```text
3
```


## Solutions

### Dart

```dart
int numDistinct(String s, String t) {
  int m = s.length;
  int n = t.length;

  List<List<int>> dp = List.generate(m + 1, (_) => List.filled(n + 1, 0));

  for (int i = 0; i <= m; i++) {
    dp[i][0] = 1;
  }

  for (int i = 1; i <= m; i++) {
    for (int j = 1; j <= n; j++) {
      if (s[i - 1] == t[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j];
      } else {
        dp[i][j] = dp[i - 1][j];
      }
    }
  }

  return dp[m][n];
}
```


### C#

```csharp
public class Solution {
    public int NumDistinct(string s, string t) {
        int m = s.Length, n = t.Length;
        int[,] dp = new int[m + 1, n + 1];

        for (int i = 0; i <= m; i++) {
            dp[i, 0] = 1;
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s[i - 1] == t[j - 1]) {
                    dp[i, j] = dp[i - 1, j - 1] + dp[i - 1, j];
                } else {
                    dp[i, j] = dp[i - 1, j];
                }
            }
        }

        return dp[m, n];
    }
}
```


### Java

```java
class Solution {
    public int numDistinct(String s, String t) {
        int m = s.length(), n = t.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 0; i <= m; i++) {
            dp[i][0] = 1;
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s.charAt(i - 1) == t.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j];
                } else {
                    dp[i][j] = dp[i - 1][j];
                }
            }
        }

        return dp[m][n];
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun numDistinct(s: String, t: String): Int {
        val m = s.length
        val n = t.length
        val dp = Array(m + 1) { IntArray(n + 1) }

        for (i in 0..m) {
            dp[i][0] = 1
        }

        for (i in 1..m) {
            for (j in 1..n) {
                if (s[i - 1] == t[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j]
                } else {
                    dp[i][j] = dp[i - 1][j]
                }
            }
        }

        return dp[m][n]
    }
}
```


### Swift

```swift
class Solution {
    func numDistinct(_ s: String, _ t: String) -> Int {
        let m = s.count, n = t.count
        var dp = Array(repeating: Array(repeating: 0, count: n + 1), count: m + 1)

        for i in 0...m {
            dp[i][0] = 1
        }

        let sArray = Array(s)
        let tArray = Array(t)

        for i in 1...m {
            for j in 1...n {
                if sArray[i - 1] == tArray[j - 1] {
                    dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j]
                } else {
                    dp[i][j] = dp[i - 1][j]
                }
            }
        }

        return dp[m][n]
    }
}
```


### The End

