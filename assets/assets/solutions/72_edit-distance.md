# Edit Distance

## Problem Statement

Given two strings `word1` and `word2`, return the minimum number of operations required to convert `word1` to `word2`.

You have the following three operations permitted on a word:
1. Insert a character
2. Delete a character
3. Replace a character

## Input

```text
word1 = "horse", word2 = "ros"
```

## Output

```text
3  
(Explanation: horse -> rorse (replace 'h' with 'r') -> rose (remove 'r') -> ros (remove 'e'))
```

## Solutions

### Dart

```dart
int minDistance(String word1, String word2) {
  int m = word1.length;
  int n = word2.length;
  List<List<int>> dp = List.generate(m + 1, (_) => List.filled(n + 1, 0));

  for (int i = 0; i <= m; i++) {
    for (int j = 0; j <= n; j++) {
      if (i == 0) {
        dp[i][j] = j;
      } else if (j == 0) {
        dp[i][j] = i;
      } else if (word1[i - 1] == word2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1];
      } else {
        dp[i][j] = 1 + math.min(dp[i - 1][j - 1], math.min(dp[i - 1][j], dp[i][j - 1]));
      }
    }
  }
  return dp[m][n];
}

void main() {
  print(minDistance("horse", "ros")); // Output: 3
  print(minDistance("intention", "execution")); // Output: 5
}
```

### C#

```csharp
public class Solution {
    public int MinDistance(string word1, string word2) {
        int m = word1.Length;
        int n = word2.Length;
        int[,] dp = new int[m + 1, n + 1];

        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                if (i == 0) {
                    dp[i, j] = j;
                } else if (j == 0) {
                    dp[i, j] = i;
                } else if (word1[i - 1] == word2[j - 1]) {
                    dp[i, j] = dp[i - 1, j - 1];
                } else {
                    dp[i, j] = 1 + Math.Min(dp[i - 1, j - 1], Math.Min(dp[i - 1, j], dp[i, j - 1]));
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
    public int minDistance(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                if (i == 0) {
                    dp[i][j] = j;
                } else if (j == 0) {
                    dp[i][j] = i;
                } else if (word1.charAt(i - 1) == word2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = 1 + Math.min(dp[i - 1][j - 1], Math.min(dp[i - 1][j], dp[i][j - 1]));
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
    fun minDistance(word1: String, word2: String): Int {
        val m = word1.length
        val n = word2.length
        val dp = Array(m + 1) { IntArray(n + 1) }

        for (i in 0..m) {
            for (j in 0..n) {
                if (i == 0) {
                    dp[i][j] = j
                } else if (j == 0) {
                    dp[i][j] = i
                } else if (word1[i - 1] == word2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1]
                } else {
                    dp[i][j] = 1 + minOf(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1])
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
    func minDistance(_ word1: String, _ word2: String) -> Int {
        let m = word1.count
        let n = word2.count
        var dp = Array(repeating: Array(repeating: 0, count: n + 1), count: m + 1)

        for i in 0...m {
            for j in 0...n {
                if i == 0 {
                    dp[i][j] = j
                } else if j == 0 {
                    dp[i][j] = i
                } else if Array(word1)[i - 1] == Array(word2)[j - 1] {
                    dp[i][j] = dp[i - 1][j - 1]
                } else {
                    dp[i][j] = 1 + min(dp[i - 1][j - 1], min(dp[i - 1][j], dp[i][j - 1]))
                }
            }
        }
        return dp[m][n]
    }
}

let solution = Solution()
print(solution.minDistance("horse", "ros")) // Output: 3
print(solution.minDistance("intention", "execution")) // Output: 5
```

### The End
