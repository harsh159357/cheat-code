# Ones and Zeroes

## Problem Statement

You are given an array of binary strings `strs` and two integers `m` and `n`.

Return the maximum number of strings you can form with `m` 0's and `n` 1's. Each 0 and 1 can only be used once in a string.

## Input

```text
strs = ["10", "0001", "111001", "1", "0"]
m = 5
n = 3
```

## Output

```text
4
```

## Solutions

### Dart

```dart
int findMaxForm(List<String> strs, int m, int n) {
  List<List<int>> dp = List.generate(m + 1, (_) => List.filled(n + 1, 0));

  for (String str in strs) {
    int zeros = str.split('0').length - 1;
    int ones = str.length - zeros;

    for (int i = m; i >= zeros; i--) {
      for (int j = n; j >= ones; j--) {
        dp[i][j] = dp[i][j].max(dp[i - zeros][j - ones] + 1);
      }
    }
  }

  return dp[m][n];
}

extension Max on int {
  int max(int other) => this > other ? this : other;
}

void main() {
  List<String> strs = ["10", "0001", "111001", "1", "0"];
  int m = 5, n = 3;
  print("Maximum number of strings: ${findMaxForm(strs, m, n)}"); // Output: 4
}
```

### C#

```csharp
public class Solution {
    public int FindMaxForm(string[] strs, int m, int n) {
        int[,] dp = new int[m + 1, n + 1];

        foreach (string str in strs) {
            int zeros = str.Count(c => c == '0');
            int ones = str.Length - zeros;

            for (int i = m; i >= zeros; i--) {
                for (int j = n; j >= ones; j--) {
                    dp[i, j] = Math.Max(dp[i, j], dp[i - zeros, j - ones] + 1);
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
    public int findMaxForm(String[] strs, int m, int n) {
        int[][] dp = new int[m + 1][n + 1];

        for (String str : strs) {
            int zeros = (int) str.chars().filter(c -> c == '0').count();
            int ones = str.length() - zeros;

            for (int i = m; i >= zeros; i--) {
                for (int j = n; j >= ones; j--) {
                    dp[i][j] = Math.max(dp[i][j], dp[i - zeros][j - ones] + 1);
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
    fun findMaxForm(strs: Array<String>, m: Int, n: Int): Int {
        val dp = Array(m + 1) { IntArray(n + 1) }

        for (str in strs) {
            val zeros = str.count { it == '0' }
            val ones = str.length - zeros

            for (i in m downTo zeros) {
                for (j in n downTo ones) {
                    dp[i][j] = maxOf(dp[i][j], dp[i - zeros][j - ones] + 1)
                }
            }
        }

        return dp[m][n]
    }
}

fun main() {
    val solution = Solution()
    val strs = arrayOf("10", "0001", "111001", "1", "0")
    val m = 5
    val n = 3
    println("Maximum number of strings: ${solution.findMaxForm(strs, m, n)}") // Output: 4
}
```

### Swift

```swift
class Solution {
    func findMaxForm(_ strs: [String], _ m: Int, _ n: Int) -> Int {
        var dp = Array(repeating: Array(repeating: 0, count: n + 1), count: m + 1)

        for str in strs {
            let zeros = str.filter { $0 == "0" }.count
            let ones = str.count - zeros

            for i in stride(from: m, through: zeros, by: -1) {
                for j in stride(from: n, through: ones, by: -1) {
                    dp[i][j] = max(dp[i][j], dp[i - zeros][j - ones] + 1)
                }
            }
        }

        return dp[m][n]
    }
}

// Example usage
let solution = Solution()
let strs = ["10", "0001", "111001", "1", "0"]
let m = 5, n = 3
print("Maximum number of strings: \(solution.findMaxForm(strs, m, n))") // Output: 4
```

### The End