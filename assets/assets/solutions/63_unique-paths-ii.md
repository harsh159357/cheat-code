# Unique Paths II

## Problem Statement

A robot is located at the top-left corner of a `m x n` grid. The robot can only move either down or right at any point in time. The grid also contains obstacles represented by `1`. The robot is trying to reach the bottom-right corner of the grid.

How many possible unique paths are there?

## Input

```text
obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
```

## Output

```text
2  
(Explanation: There are two unique paths to reach the bottom-right corner avoiding the obstacles.)
```

## Solutions

### Dart

```dartd
int uniquePathsWithObstacles(List<List<int>> obstacleGrid) {
  int m = obstacleGrid.length;
  int n = obstacleGrid[0].length;
  List<int> dp = List.filled(n, 0);
  dp[0] = obstacleGrid[0][0] == 1 ? 0 : 1;

  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (obstacleGrid[i][j] == 1) {
        dp[j] = 0;
      } else if (j > 0) {
        dp[j] += dp[j - 1];
      }
    }
  }

  return dp[n - 1];
}

void main() {
  print(uniquePathsWithObstacles([
    [0, 0, 0],
    [0, 1, 0],
    [0, 0, 0]
  ])); // Output: 2
}
```

### C#

```csharp
public class Solution {
    public int UniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.Length;
        int n = obstacleGrid[0].Length;
        int[] dp = new int[n];
        dp[0] = obstacleGrid[0][0] == 1 ? 0 : 1;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (obstacleGrid[i][j] == 1) {
                    dp[j] = 0;
                } else if (j > 0) {
                    dp[j] += dp[j - 1];
                }
            }
        }

        return dp[n - 1];
    }
}
```

### Java

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        int[] dp = new int[n];
        dp[0] = obstacleGrid[0][0] == 1 ? 0 : 1;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (obstacleGrid[i][j] == 1) {
                    dp[j] = 0;
                } else if (j > 0) {
                    dp[j] += dp[j - 1];
                }
            }
        }

        return dp[n - 1];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun uniquePathsWithObstacles(obstacleGrid: Array<IntArray>): Int {
        val m = obstacleGrid.size
        val n = obstacleGrid[0].size
        val dp = IntArray(n)
        dp[0] = if (obstacleGrid[0][0] == 1) 0 else 1

        for (i in 0 until m) {
            for (j in 0 until n) {
                if (obstacleGrid[i][j] == 1) {
                    dp[j] = 0
                } else if (j > 0) {
                    dp[j] += dp[j - 1]
                }
            }
        }

        return dp[n - 1]
    }
}
```

### Swift

```swift
class Solution {
    func uniquePathsWithObstacles(_ obstacleGrid: [[Int]]) -> Int {
        let m = obstacleGrid.count
        let n = obstacleGrid[0].count
        var dp = [Int](repeating: 0, count: n)
        dp[0] = obstacleGrid[0][0] == 1 ? 0 : 1

        for i in 0..<m {
            for j in 0..<n {
                if obstacleGrid[i][j] == 1 {
                    dp[j] = 0
                } else if j > 0 {
                    dp[j] += dp[j - 1]
                }
            }
        }

        return dp[n - 1]
    }
}

let solution = Solution()
print(solution.uniquePathsWithObstacles([
    [0, 0, 0],
    [0, 1, 0],
    [0, 0, 0]
])) // Output: 2
```

### The End

