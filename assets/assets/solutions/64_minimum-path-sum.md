# Minimum Path Sum

## Problem Statement

Given a `m x n` grid filled with non-negative numbers, find a path from the top-left to the bottom-right, which minimizes the sum of all numbers along its path.

You can only move either down or right at any point in time.

## Input

```text
grid = [[1,3,1],[1,5,1],[4,2,1]]
```

## Output

```text
7  
(Explanation: The path 1 → 3 → 1 → 1 → 1 minimizes the sum.)
```

## Solutions

### Dart

```dart
int minPathSum(List<List<int>> grid) {
  int m = grid.length;
  int n = grid[0].length;

  for (int i = 1; i < m; i++) {
    grid[i][0] += grid[i - 1][0];
  }

  for (int j = 1; j < n; j++) {
    grid[0][j] += grid[0][j - 1];
  }

  for (int i = 1; i < m; i++) {
    for (int j = 1; j < n; j++) {
      grid[i][j] += math.min(grid[i - 1][j], grid[i][j - 1]);
    }
  }

  return grid[m - 1][n - 1];
}

void main() {
  print(minPathSum([
    [1, 3, 1],
    [1, 5, 1],
    [4, 2, 1]
  ])); // Output: 7
}
```

### C#

```csharp
public class Solution {
    public int MinPathSum(int[][] grid) {
        int m = grid.Length;
        int n = grid[0].Length;

        for (int i = 1; i < m; i++) {
            grid[i][0] += grid[i - 1][0];
        }

        for (int j = 1; j < n; j++) {
            grid[0][j] += grid[0][j - 1];
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                grid[i][j] += Math.Min(grid[i - 1][j], grid[i][j - 1]);
            }
        }

        return grid[m - 1][n - 1];
    }
}
```

### Java

```java
class Solution {
    public int minPathSum(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        for (int i = 1; i < m; i++) {
            grid[i][0] += grid[i - 1][0];
        }

        for (int j = 1; j < n; j++) {
            grid[0][j] += grid[0][j - 1];
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                grid[i][j] += Math.min(grid[i - 1][j], grid[i][j - 1]);
            }
        }

        return grid[m - 1][n - 1];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun minPathSum(grid: Array<IntArray>): Int {
        val m = grid.size
        val n = grid[0].size

        for (i in 1 until m) {
            grid[i][0] += grid[i - 1][0]
        }

        for (j in 1 until n) {
            grid[0][j] += grid[0][j - 1]
        }

        for (i in 1 until m) {
            for (j in 1 until n) {
                grid[i][j] += minOf(grid[i - 1][j], grid[i][j - 1])
            }
        }

        return grid[m - 1][n - 1]
    }
}
```

### Swift

```swift
class Solution {
    func minPathSum(_ grid: [[Int]]) -> Int {
        var grid = grid
        let m = grid.count
        let n = grid[0].count

        for i in 1..<m {
            grid[i][0] += grid[i - 1][0]
        }

        for j in 1..<n {
            grid[0][j] += grid[0][j - 1]
        }

        for i in 1..<m {
            for j in 1..<n {
                grid[i][j] += min(grid[i - 1][j], grid[i][j - 1])
            }
        }

        return grid[m - 1][n - 1]
    }
}

let solution = Solution()
print(solution.minPathSum([
    [1, 3, 1],
    [1, 5, 1],
    [4, 2, 1]
])) // Output: 7
```

### The End

