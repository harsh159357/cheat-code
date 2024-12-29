# Longest Common Subsequence

## Problem Statement

Given two strings `text1` and `text2`, return the length of their longest common subsequence.  
A subsequence is a sequence that appears in the same relative order but not necessarily contiguous.

---

## Input

```text
text1 = "abcde", text2 = "ace"
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun longestCommonSubsequence(text1: String, text2: String): Int {
        val m = text1.length
        val n = text2.length
        val dp = Array(m + 1) { IntArray(n + 1) }
        
        for (i in 1..m) {
            for (j in 1..n) {
                if (text1[i - 1] == text2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1
                } else {
                    dp[i][j] = maxOf(dp[i - 1][j], dp[i][j - 1])
                }
            }
        }
        return dp[m][n]
    }
}

fun main() {
    val solution = Solution()
    println(solution.longestCommonSubsequence("abcde", "ace")) // Output: 3
}
```


### Dart

```dart
int longestCommonSubsequence(String text1, String text2) {
  int m = text1.length;
  int n = text2.length;
  List<List<int>> dp = List.generate(m + 1, (_) => List.filled(n + 1, 0));

  for (int i = 1; i <= m; i++) {
    for (int j = 1; j <= n; j++) {
      if (text1[i - 1] == text2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + 1;
      } else {
        dp[i][j] = dp[i - 1][j].max(dp[i][j - 1]);
      }
    }
  }
  return dp[m][n];
}

void main() {
  print(longestCommonSubsequence("abcde", "ace")); // Output: 3
}
```


### C#

```csharp
public class Solution {
    public int LongestCommonSubsequence(string text1, string text2) {
        int m = text1.Length;
        int n = text2.Length;
        int[,] dp = new int[m + 1, n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1[i - 1] == text2[j - 1]) {
                    dp[i, j] = dp[i - 1, j - 1] + 1;
                } else {
                    dp[i, j] = Math.Max(dp[i - 1, j], dp[i, j - 1]);
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
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        return dp[m][n];
    }
}
```


### Swift

```swift
class Solution {
    func longestCommonSubsequence(_ text1: String, _ text2: String) -> Int {
        let m = text1.count
        let n = text2.count
        var dp = Array(repeating: Array(repeating: 0, count: n + 1), count: m + 1)
        
        let t1 = Array(text1)
        let t2 = Array(text2)
        
        for i in 1...m {
            for j in 1...n {
                if t1[i - 1] == t2[j - 1] {
                    dp[i][j] = dp[i - 1][j - 1] + 1
                } else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
                }
            }
        }
        return dp[m][n]
    }
}

let solution = Solution()
print(solution.longestCommonSubsequence("abcde", "ace")) // Output: 3
```

### The End