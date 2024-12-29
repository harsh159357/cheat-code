# Number of Enclaves

## Problem Statement

You are given an `m x n` binary matrix `grid`, where `0` represents water and `1` represents land. A move consists of walking from one land cell to another adjacent (4-directionally) land cell or walking off the boundary of the grid.

Return the number of land cells in `grid` for which we cannot walk off the boundary of the grid in any number of moves.

## Input

```text
grid = [[0,0,0,0],
        [1,0,1,0],
        [0,1,1,0],
        [0,0,0,0]]
```

## Output

```text
Number of enclaves: 3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun numEnclaves(grid: Array<IntArray>): Int {
        val m = grid.size
        val n = grid[0].size
        
        fun dfs(x: Int, y: Int) {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] != 1) return
            grid[x][y] = 0 // Mark as visited
            dfs(x + 1, y)
            dfs(x - 1, y)
            dfs(x, y + 1)
            dfs(x, y - 1)
        }

        for (i in 0 until m) {
            dfs(i, 0)
            dfs(i, n - 1)
        }
        for (j in 0 until n) {
            dfs(0, j)
            dfs(m - 1, j)
        }

        var count = 0
        for (i in 0 until m) {
            for (j in 0 until n) {
                if (grid[i][j] == 1) count++
            }
        }

        return count
    }
}
```

### Dart

```dart
int numEnclaves(List<List<int>> grid) {
  int m = grid.length, n = grid[0].length;

  void dfs(int x, int y) {
    if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] != 1) return;
    grid[x][y] = 0;
    dfs(x + 1, y);
    dfs(x - 1, y);
    dfs(x, y + 1);
    dfs(x, y - 1);
  }

  for (int i = 0; i < m; i++) {
    dfs(i, 0);
    dfs(i, n - 1);
  }
  for (int j = 0; j < n; j++) {
    dfs(0, j);
    dfs(m - 1, j);
  }

  int count = 0;
  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (grid[i][j] == 1) count++;
    }
  }

  return count;
}
```

### C#

```csharp
public class Solution {
    public int NumEnclaves(int[][] grid) {
        int m = grid.Length, n = grid[0].Length;

        void Dfs(int x, int y) {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] != 1) return;
            grid[x][y] = 0;
            Dfs(x + 1, y);
            Dfs(x - 1, y);
            Dfs(x, y + 1);
            Dfs(x, y - 1);
        }

        for (int i = 0; i < m; i++) {
            Dfs(i, 0);
            Dfs(i, n - 1);
        }
        for (int j = 0; j < n; j++) {
            Dfs(0, j);
            Dfs(m - 1, j);
        }

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1) count++;
            }
        }

        return count;
    }
}
```

### Java

```java
class Solution {
    public int numEnclaves(int[][] grid) {
        int m = grid.length, n = grid[0].length;

        void dfs(int x, int y) {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] != 1) return;
            grid[x][y] = 0;
            dfs(x + 1, y);
            dfs(x - 1, y);
            dfs(x, y + 1);
            dfs(x, y - 1);
        }

        for (int i = 0; i < m; i++) {
            dfs(i, 0);
            dfs(i, n - 1);
        }
        for (int j = 0; j < n; j++) {
            dfs(0, j);
            dfs(m - 1, j);
        }

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1) count++;
            }
        }

        return count;
    }
}
```

### Swift

```swift
class Solution {
    func numEnclaves(_ grid: [[Int]]) -> Int {
        var grid = grid
        let m = grid.count
        let n = grid[0].count

        func dfs(_ x: Int, _ y: Int) {
            if x < 0 || x >= m || y < 0 || y >= n || grid[x][y] != 1 { return }
            grid[x][y] = 0
            dfs(x + 1, y)
            dfs(x - 1, y)
            dfs(x, y + 1)
            dfs(x, y - 1)
        }

        for i in 0..<m {
            dfs(i, 0)
            dfs(i, n - 1)
        }
        for j in 0..<n {
            dfs(0, j)
            dfs(m - 1, j)
        }

        var count = 0
        for i in 0..<m {
            for j in 0..<n {
                if grid[i][j] == 1 { count += 1 }
            }
        }

        return count
    }
}
```

### The End