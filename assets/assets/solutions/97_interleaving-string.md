# Interleaving String

## Problem Statement

Given strings `s1`, `s2`, and `s3`, determine whether `s3` is formed by an interleaving of `s1` and `s2`.

An interleaving of two strings `s1` and `s2` is a string that contains all the characters of `s1` and `s2` and preserves the order of characters from each string.

## Input

```text
s1 = "aab"
s2 = "axy"
s3 = "aaxaby"
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool isInterleave(String s1, String s2, String s3) {
  if (s1.length + s2.length != s3.length) return false;
  List<List<bool>> dp = List.generate(s1.length + 1, (_) => List.filled(s2.length + 1, false));

  for (int i = 0; i <= s1.length; i++) {
    for (int j = 0; j <= s2.length; j++) {
      if (i == 0 && j == 0) {
        dp[i][j] = true;
      } else if (i == 0) {
        dp[i][j] = dp[i][j - 1] && s2[j - 1] == s3[i + j - 1];
      } else if (j == 0) {
        dp[i][j] = dp[i - 1][j] && s1[i - 1] == s3[i + j - 1];
      } else {
        dp[i][j] = (dp[i - 1][j] && s1[i - 1] == s3[i + j - 1]) || (dp[i][j - 1] && s2[j - 1] == s3[i + j - 1]);
      }
    }
  }
  return dp[s1.length][s2.length];
}
```

### C#

```csharp
public class Solution {
    public bool IsInterleave(string s1, string s2, string s3) {
        if (s1.Length + s2.Length != s3.Length) return false;
        bool[,] dp = new bool[s1.Length + 1, s2.Length + 1];

        for (int i = 0; i <= s1.Length; i++) {
            for (int j = 0; j <= s2.Length; j++) {
                if (i == 0 && j == 0) {
                    dp[i, j] = true;
                } else if (i == 0) {
                    dp[i, j] = dp[i, j - 1] && s2[j - 1] == s3[i + j - 1];
                } else if (j == 0) {
                    dp[i, j] = dp[i - 1, j] && s1[i - 1] == s3[i + j - 1];
                } else {
                    dp[i, j] = (dp[i - 1, j] && s1[i - 1] == s3[i + j - 1]) || (dp[i, j - 1] && s2[j - 1] == s3[i + j - 1]);
                }
            }
        }
        return dp[s1.Length, s2.Length];
    }
}
```

### Java

```java
class Solution {
    public boolean isInterleave(String s1, String s2, String s3) {
        if (s1.length() + s2.length() != s3.length()) return false;
        boolean[][] dp = new boolean[s1.length() + 1][s2.length() + 1];

        for (int i = 0; i <= s1.length(); i++) {
            for (int j = 0; j <= s2.length(); j++) {
                if (i == 0 && j == 0) {
                    dp[i][j] = true;
                } else if (i == 0) {
                    dp[i][j] = dp[i][j - 1] && s2.charAt(j - 1) == s3.charAt(i + j - 1);
                } else if (j == 0) {
                    dp[i][j] = dp[i - 1][j] && s1.charAt(i - 1) == s3.charAt(i + j - 1);
                } else {
                    dp[i][j] = (dp[i - 1][j] && s1.charAt(i - 1) == s3.charAt(i + j - 1)) || (dp[i][j - 1] && s2.charAt(j - 1) == s3.charAt(i + j - 1));
                }
            }
        }
        return dp[s1.length()][s2.length()];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isInterleave(s1: String, s2: String, s3: String): Boolean {
        if (s1.length + s2.length != s3.length) return false
        val dp = Array(s1.length + 1) { BooleanArray(s2.length + 1) }
        for (i in 0..s1.length) {
            for (j in 0..s2.length) {
                if (i == 0 && j == 0) {
                    dp[i][j] = true
                } else if (i == 0) {
                    dp[i][j] = dp[i][j - 1] && s2[j - 1] == s3[i + j - 1]
                } else if (j == 0) {
                    dp[i][j] = dp[i - 1][j] && s1[i - 1] == s3[i + j - 1]
                } else {
                    dp[i][j] = (dp[i - 1][j] && s1[i - 1] == s3[i + j - 1]) || (dp[i][j - 1] && s2[j - 1] == s3[i + j - 1])
                }
            }
        }
        return dp[s1.length][s2.length]
    }
}
```

### Swift

```swift
class Solution {
    func isInterleave(_ s1: String, _ s2: String, _ s3: String) -> Bool {
        if s1.count + s2.count != s3.count { return false }
        var dp = Array(repeating: Array(repeating: false, count: s2.count + 1), count: s1.count + 1)
        for i in 0...s1.count {
            for j in 0...s2.count {
                if i == 0 && j == 0 {
                    dp[i][j] = true
                } else if i == 0 {
                    dp[i][j] = dp[i][j - 1] && s2[s2.index(s2.startIndex, offsetBy: j - 1)] == s3[s3.index(s3.startIndex, offsetBy: i + j - 1)]
                } else if j == 0 {
                    dp[i][j] = dp[i - 1][j] && s1[s1.index(s1.startIndex, offsetBy: i - 1)] == s3[s3.index(s3.startIndex, offsetBy: i + j - 1)]
                } else {
                    dp[i][j] = (dp[i - 1][j] && s1[s1.index(s1.startIndex, offsetBy: i - 1)] == s3[s3.index(s3.startIndex, offsetBy: i + j - 1)]) || 
                               (dp[i][j - 1] && s2[s2.index(s2.startIndex, offsetBy: j - 1)] == s3[s3.index(s3.startIndex, offsetBy: i + j - 1)])
                }
            }
        }
        return dp[s1.count][s2.count]
    }
}
```

### The End

