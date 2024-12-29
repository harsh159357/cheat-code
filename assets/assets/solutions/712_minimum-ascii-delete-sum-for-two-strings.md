# Minimum ASCII Delete Sum for Two Strings

## Problem Statement

Given two strings `s1` and `s2`, return the minimum ASCII sum of deleted characters to make the two strings equal.

## Input

```text
s1 = "sea", s2 = "eat"
```

## Output

```text
231
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun minimumDeleteSum(s1: String, s2: String): Int {
        val m = s1.length
        val n = s2.length

        // Create a 2D array to store the minimum ASCII delete sum for substrings
        val dp = Array(m + 1) { IntArray(n + 1) }

        // Initialize the first row and column
        for (i in 1..m) {
            dp[i][0] = dp[i - 1][0] + s1[i - 1].toInt()
        }
        for (j in 1..n) {
            dp[0][j] = dp[0][j - 1] + s2[j - 1].toInt()
        }

        // Fill the dp array
        for (i in 1..m) {
            for (j in 1..n) {
                if (s1[i - 1] == s2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1]
                } else {
                    dp[i][j] = minOf(
                        dp[i - 1][j] + s1[i - 1].toInt(),
                        dp[i][j - 1] + s2[j - 1].toInt()
                    )
                }
            }
        }

        // Return the value in the bottom-right cell
        return dp[m][n]
    }
}

fun main() {
    val s1 = "sea"
    val s2 = "eat"
    val solution = Solution()
    println("Minimum ASCII delete sum: ${solution.minimumDeleteSum(s1, s2)}") // Output: 231
}
```


### Dart

```dart
int minimumDeleteSum(String s1, String s2) {
  int m = s1.length;
  int n = s2.length;

  // Create a 2D array
  List<List<int>> dp = List.generate(m + 1, (_) => List.filled(n + 1, 0));

  // Initialize the first row and column
  for (int i = 1; i <= m; i++) {
    dp[i][0] = dp[i - 1][0] + s1.codeUnitAt(i - 1);
  }
  for (int j = 1; j <= n; j++) {
    dp[0][j] = dp[0][j - 1] + s2.codeUnitAt(j - 1);
  }

  // Fill the dp array
  for (int i = 1; i <= m; i++) {
    for (int j = 1; j <= n; j++) {
      if (s1[i - 1] == s2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1];
      } else {
        dp[i][j] = (dp[i - 1][j] + s1.codeUnitAt(i - 1))
            .min(dp[i][j - 1] + s2.codeUnitAt(j - 1));
      }
    }
  }

  return dp[m][n];
}

extension on int {
  int min(int other) => this < other ? this : other;
}

void main() {
  String s1 = "sea";
  String s2 = "eat";
  print("Minimum ASCII delete sum: ${minimumDeleteSum(s1, s2)}"); // Output: 231
}
```


### C#

```csharp
public class Solution {
    public int MinimumDeleteSum(string s1, string s2) {
        int m = s1.Length, n = s2.Length;
        int[,] dp = new int[m + 1, n + 1];

        for (int i = 1; i <= m; i++) {
            dp[i, 0] = dp[i - 1, 0] + s1[i - 1];
        }
        for (int j = 1; j <= n; j++) {
            dp[0, j] = dp[0, j - 1] + s2[j - 1];
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s1[i - 1] == s2[j - 1]) {
                    dp[i, j] = dp[i - 1, j - 1];
                } else {
                    dp[i, j] = Math.Min(dp[i - 1, j] + s1[i - 1], dp[i, j - 1] + s2[j - 1]);
                }
            }
        }

        return dp[m, n];
    }
}
```


### Swift

```swift
class Solution {
    func minimumDeleteSum(_ s1: String, _ s2: String) -> Int {
        let s1 = Array(s1)
        let s2 = Array(s2)
        let m = s1.count
        let n = s2.count
        var dp = Array(repeating: Array(repeating: 0, count: n + 1), count: m + 1)

        for i in 1...m {
            dp[i][0] = dp[i - 1][0] + Int(s1[i - 1].asciiValue!)
        }
        for j in 1...n {
            dp[0][j] = dp[0][j - 1] + Int(s2[j - 1].asciiValue!)
        }

        for i in 1...m {
            for j in 1...n {
                if s1[i - 1] == s2[j - 1] {
                    dp[i][j] = dp[i - 1][j - 1]
                } else {
                    dp[i][j] = min(dp[i - 1][j] + Int(s1[i - 1].asciiValue!), dp[i][j - 1] + Int(s2[j - 1].asciiValue!))
                }
            }
        }

        return dp[m][n]
    }
}

// Example usage
let solution = Solution()
print("Minimum ASCII delete sum: \(solution.minimumDeleteSum("sea", "eat"))") // Output: 231
```

### The End