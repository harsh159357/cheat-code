# Longest Palindromic Subsequence

## Problem Statement

Given a string `s`, find the length of its longest palindromic subsequence. A subsequence is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.

## Input

```text
s = "bbbab"
```

## Output

```text
4
```

## Solutions

### Dart

```dart
int longestPalindromeSubseq(String s) {
  int n = s.length;

  // Create a 2D list to store the length of the longest palindromic subsequence
  List<List<int>> dp = List.generate(n, (_) => List.filled(n, 0));

  // Each single character is a palindrome of length 1
  for (int i = 0; i < n; i++) {
    dp[i][i] = 1;
  }

  // Fill the dp array for substrings of increasing lengths
  for (int len = 2; len <= n; len++) {
    for (int i = 0; i <= n - len; i++) {
      int j = i + len - 1;
      if (s[i] == s[j]) {
        dp[i][j] = dp[i + 1][j - 1] + 2;
      } else {
        dp[i][j] = dp[i + 1][j].max(dp[i][j - 1]);
      }
    }
  }

  // The result is stored in dp[0][n - 1]
  return dp[0][n - 1];
}

extension Max on int {
  int max(int other) => this > other ? this : other;
}

void main() {
  print(longestPalindromeSubseq("bbbab")); // Output: 4
}
```

### C#

```csharp
public class Solution {
    public int LongestPalindromeSubseq(string s) {
        int n = s.Length;

        // Create a 2D array to store the length of the longest palindromic subsequence
        int[,] dp = new int[n, n];

        // Each single character is a palindrome of length 1
        for (int i = 0; i < n; i++) {
            dp[i, i] = 1;
        }

        // Fill the dp array for substrings of increasing lengths
        for (int len = 2; len <= n; len++) {
            for (int i = 0; i <= n - len; i++) {
                int j = i + len - 1;
                if (s[i] == s[j]) {
                    dp[i, j] = dp[i + 1, j - 1] + 2;
                } else {
                    dp[i, j] = Math.Max(dp[i + 1, j], dp[i, j - 1]);
                }
            }
        }

        // The result is stored in dp[0, n - 1]
        return dp[0, n - 1];
    }
}
```

### Java

```java
class Solution {
    public int longestPalindromeSubseq(String s) {
        int n = s.length();

        // Create a 2D array to store the length of the longest palindromic subsequence
        int[][] dp = new int[n][n];

        // Each single character is a palindrome of length 1
        for (int i = 0; i < n; i++) {
            dp[i][i] = 1;
        }

        // Fill the dp array for substrings of increasing lengths
        for (int len = 2; len <= n; len++) {
            for (int i = 0; i <= n - len; i++) {
                int j = i + len - 1;
                if (s.charAt(i) == s.charAt(j)) {
                    dp[i][j] = dp[i + 1][j - 1] + 2;
                } else {
                    dp[i][j] = Math.max(dp[i + 1][j], dp[i][j - 1]);
                }
            }
        }

        // The result is stored in dp[0][n - 1]
        return dp[0][n - 1];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun longestPalindromeSubseq(s: String): Int {
        val n = s.length

        // Create a 2D array to store the length of the longest palindromic subsequence
        val dp = Array(n) { IntArray(n) }

        // Each single character is a palindrome of length 1
        for (i in 0 until n) {
            dp[i][i] = 1
        }

        // Fill the dp array for substrings of increasing lengths
        for (len in 2..n) {
            for (i in 0..n - len) {
                val j = i + len - 1
                if (s[i] == s[j]) {
                    dp[i][j] = dp[i + 1][j - 1] + 2
                } else {
                    dp[i][j] = maxOf(dp[i + 1][j], dp[i][j - 1])
                }
            }
        }

        // The result is stored in dp[0][n - 1]
        return dp[0][n - 1]
    }
}

fun main() {
    val solution = Solution()
    println(solution.longestPalindromeSubseq("bbbab")) // Output: 4
}
```

### Swift

```swift
class Solution {
    func longestPalindromeSubseq(_ s: String) -> Int {
        let n = s.count
        let chars = Array(s)
        var dp = Array(repeating: Array(repeating: 0, count: n), count: n)

        // Each single character is a palindrome of length 1
        for i in 0..<n {
            dp[i][i] = 1
        }

        // Fill the dp array for substrings of increasing lengths
        for len in 2...n {
            for i in 0...(n - len) {
                let j = i + len - 1
                if chars[i] == chars[j] {
                    dp[i][j] = dp[i + 1][j - 1] + 2
                } else {
                    dp[i][j] = max(dp[i + 1][j], dp[i][j - 1])
                }
            }
        }

        // The result is stored in dp[0][n - 1]
        return dp[0][n - 1]
    }
}

// Example usage
let solution = Solution()
print(solution.longestPalindromeSubseq("bbbab")) // Output: 4
```

### The End