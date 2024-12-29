# Minimum Insertion Steps to Make a String Palindrome

## Problem Statement

Given a string `s`, return the minimum number of insertions needed to make `s` a palindrome.

## Input

```text
s = "mbadm"
```

## Output

```text
2
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun minInsertions(s: String): Int {
        fun longestCommonSubsequence(s1: String, s2: String): Int {
            val m = s1.length
            val n = s2.length
            val dp = Array(m + 1) { IntArray(n + 1) }

            for (i in 1..m) {
                for (j in 1..n) {
                    dp[i][j] = if (s1[i - 1] == s2[j - 1]) {
                        dp[i - 1][j - 1] + 1
                    } else {
                        maxOf(dp[i - 1][j], dp[i][j - 1])
                    }
                }
            }
            return dp[m][n]
        }

        return s.length - longestCommonSubsequence(s, s.reversed())
    }
}
```

### Dart

```dart
int minInsertions(String s) {
  int longestCommonSubsequence(String s1, String s2) {
    int m = s1.length, n = s2.length;
    List<List<int>> dp = List.generate(m + 1, (_) => List.filled(n + 1, 0));

    for (int i = 1; i <= m; i++) {
      for (int j = 1; j <= n; j++) {
        if (s1[i - 1] == s2[j - 1]) {
          dp[i][j] = dp[i - 1][j - 1] + 1;
        } else {
          dp[i][j] = dp[i - 1][j].max(dp[i][j - 1]);
        }
      }
    }
    return dp[m][n];
  }

  return s.length - longestCommonSubsequence(s, s.split('').reversed.join());
}
```

### C#

```csharp
public class Solution {
    public int MinInsertions(string s) {
        int LongestCommonSubsequence(string s1, string s2) {
            int m = s1.Length, n = s2.Length;
            int[,] dp = new int[m + 1, n + 1];

            for (int i = 1; i <= m; i++) {
                for (int j = 1; j <= n; j++) {
                    dp[i, j] = s1[i - 1] == s2[j - 1] 
                        ? dp[i - 1, j - 1] + 1 
                        : Math.Max(dp[i - 1, j], dp[i, j - 1]);
                }
            }
            return dp[m, n];
        }

        return s.Length - LongestCommonSubsequence(s, new string(s.Reverse().ToArray()));
    }
}
```

### Java

```java
class Solution {
    public int minInsertions(String s) {
        int longestCommonSubsequence(String s1, String s2) {
            int m = s1.length(), n = s2.length();
            int[][] dp = new int[m + 1][n + 1];

            for (int i = 1; i <= m; i++) {
                for (int j = 1; j <= n; j++) {
                    if (s1.charAt(i - 1) == s2.charAt(j - 1)) {
                        dp[i][j] = dp[i - 1][j - 1] + 1;
                    } else {
                        dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                    }
                }
            }
            return dp[m][n];
        }

        return s.length() - longestCommonSubsequence(s, new StringBuilder(s).reverse().toString());
    }
}
```

### Swift

```swift
class Solution {
    func minInsertions(_ s: String) -> Int {
        func longestCommonSubsequence(_ s1: [Character], _ s2: [Character]) -> Int {
            let m = s1.count, n = s2.count
            var dp = Array(repeating: Array(repeating: 0, count: n + 1), count: m + 1)

            for i in 1...m {
                for j in 1...n {
                    if s1[i - 1] == s2[j - 1] {
                        dp[i][j] = dp[i - 1][j - 1] + 1
                    } else {
                        dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
                    }
                }
            }
            return dp[m][n]
        }

        let s1 = Array(s)
        let s2 = Array(s.reversed())
        return s.count - longestCommonSubsequence(s1, s2)
    }
}
```

### The End