# Unique Paths

## Problem Statement

A robot is located at the top-left corner of a `m x n` grid. The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid.

How many possible unique paths are there?

## Input

```text
m = 3, n = 7
```

## Output

```text
28  
(Explanation: There are 28 unique paths to reach the bottom-right corner.)
```

## Solutions

### Dart

```dart
int uniquePaths(int m, int n) {
  List<int> dp = List.filled(n, 1);

  for (int i = 1; i < m; i++) {
    for (int j = 1; j < n; j++) {
      dp[j] += dp[j - 1];
    }
  }

  return dp[n - 1];
}

void main() {
  print(uniquePaths(3, 7)); // Output: 28
  print(uniquePaths(3, 2)); // Output: 3
}
```

### C#

```csharp
public class Solution {
    public int UniquePaths(int m, int n) {
        int[] dp = new int[n];
        for (int i = 0; i < n; i++) {
            dp[i] = 1;
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[j] += dp[j - 1];
            }
        }

        return dp[n - 1];
    }
}
```

### Java

```java
class Solution {
    public int uniquePaths(int m, int n) {
        int[] dp = new int[n];
        for (int i = 0; i < n; i++) {
            dp[i] = 1;
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[j] += dp[j - 1];
            }
        }

        return dp[n - 1];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun uniquePaths(m: Int, n: Int): Int {
        require(!(m == 0 || n == 0)) { "m or n can't be 0" }
        val dp = IntArray(n) { 1 }

        for (i in 1 until m) {
            for (j in 1 until n) {
                dp[j] += dp[j - 1]
            }
        }

        return dp[n - 1]
    }
}
```

### Swift

```swift
class Solution {
    func uniquePaths(_ m: Int, _ n: Int) -> Int {
        var dp = [Int](repeating: 1, count: n)

        for _ in 1..<m {
            for j in 1..<n {
                dp[j] += dp[j - 1]
            }
        }

        return dp[n - 1]
    }
}

let solution = Solution()
print(solution.uniquePaths(3, 7)) // Output: 28
print(solution.uniquePaths(3, 2)) // Output: 3
```

### The End

