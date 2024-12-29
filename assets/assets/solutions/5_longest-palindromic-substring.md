# Longest Palindromic Substring

## Problem Statement

Given a string `s`, return the longest palindromic substring in `s`.

## Input

```text
s = "babad"
```

## Output

```text
"bab"  
(Note: "aba" is also a valid answer.)
```

## Solutions

### Dart

```dart
String longestPalindrome(String s) {
  int n = s.length;
  List<List<bool>> dp = List.generate(n, (_) => List.filled(n, false));
  int start = 0, maxLen = 1;

  for (int i = 0; i < n; i++) {
    dp[i][i] = true;
  }

  for (int len = 2; len <= n; len++) {
    for (int i = 0; i < n - len + 1; i++) {
      int j = i + len - 1;
      if (s[i] == s[j] && (len == 2 || dp[i + 1][j - 1])) {
        dp[i][j] = true;
        if (len > maxLen) {
          start = i;
          maxLen = len;
        }
      }
    }
  }

  return s.substring(start, start + maxLen);
}

void main() {
  print(longestPalindrome("babad")); // Output: "bab" or "aba"
}
```

### C#

```csharp
public class Solution {
    public string LongestPalindrome(string s) {
        int n = s.Length;
        bool[,] dp = new bool[n, n];
        int start = 0, maxLen = 1;

        for (int i = 0; i < n; i++) {
            dp[i, i] = true;
        }

        for (int len = 2; len <= n; len++) {
            for (int i = 0; i < n - len + 1; i++) {
                int j = i + len - 1;
                if (s[i] == s[j] && (len == 2 || dp[i + 1, j - 1])) {
                    dp[i, j] = true;
                    if (len > maxLen) {
                        start = i;
                        maxLen = len;
                    }
                }
            }
        }

        return s.Substring(start, maxLen);
    }
}
```

### Java

```java
class Solution {
    public String longestPalindrome(String s) {
        int n = s.length();
        boolean[][] dp = new boolean[n][n];
        int start = 0, maxLen = 1;

        for (int i = 0; i < n; i++) {
            dp[i][i] = true;
        }

        for (int len = 2; len <= n; len++) {
            for (int i = 0; i < n - len + 1; i++) {
                int j = i + len - 1;
                if (s.charAt(i) == s.charAt(j) && (len == 2 || dp[i + 1][j - 1])) {
                    dp[i][j] = true;
                    if (len > maxLen) {
                        start = i;
                        maxLen = len;
                    }
                }
            }
        }

        return s.substring(start, start + maxLen);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun longestPalindrome(s: String): String {
        val n = s.length
        val dp = Array(n) { BooleanArray(n) }
        var start = 0
        var maxLen = 1
        for (i in 0 until n) {
            dp[i][i] = true
        }
        for (len in 2..n) {
            for (i in 0 until n - len + 1) {
                val j = i + len - 1
                if (s[i] == s[j] && (len == 2 || dp[i + 1][j - 1])) {
                    dp[i][j] = true
                    if (len > maxLen) {
                        start = i
                        maxLen = len
                    }
                }
            }
        }
        return s.substring(start, start + maxLen)
    }
}
```

### Swift

```swift
class Solution {
    func longestPalindrome(_ s: String) -> String {
        let n = s.count
        var dp = Array(repeating: Array(repeating: false, count: n), count: n)
        var start = 0
        var maxLen = 1

        for i in 0..<n {
            dp[i][i] = true
        }

        for len in 2...n {
            for i in 0..<(n - len + 1) {
                let j = i + len - 1
                if Array(s)[i] == Array(s)[j] && (len == 2 || dp[i + 1][j - 1]) {
                    dp[i][j] = true
                    if len > maxLen {
                        start = i
                        maxLen = len
                    }
                }
            }
        }

        let startIdx = s.index(s.startIndex, offsetBy: start)
        let endIdx = s.index(s.startIndex, offsetBy: start + maxLen)
        return String(s[startIdx..<endIdx])
    }
}
```

### The End

