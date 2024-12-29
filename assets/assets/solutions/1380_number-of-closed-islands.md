# Number of Closed Islands

## Problem Statement

Given a 2D grid consisting of `0`s (land) and `1`s (water), return the number of closed islands. A **closed island** is a group of `0`s completely surrounded by `1`s in all 4 directions.

## Input

```text
grid = [
    [1,1,1,1,0,1,1,1,1,1],
    [1,0,1,1,0,1,0,1,1,1],
    [1,1,0,1,1,0,0,1,1,1],
    [0,0,0,1,1,0,1,1,1,1],
    [0,1,0,0,0,1,1,1,1,1],
    [0,0,1,0,0,0,0,1,1,1],
    [0,1,0,0,1,0,0,1,1,1],
    [1,1,1,1,1,1,1,1,1,1]
]
```

## Output

```text
Number of closed islands: 2
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun closedIsland(grid: Array<IntArray>): Int {
        val m = grid.size
        val n = grid[0].size

        fun dfs(x: Int, y: Int) {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 1) return
            grid[x][y] = 1
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
                if (grid[i][j] == 0) {
                    count++
                    dfs(i, j)
                }
            }
        }
        return count
    }
}
```

### Dart

```dart
int closedIsland(List<List<int>> grid) {
  int m = grid.length;
  int n = grid[0].length;

  void dfs(int x, int y) {
    if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 1) return;
    grid[x][y] = 1;
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
      if (grid[i][j] == 0) {
        count++;
        dfs(i, j);
      }
    }
  }
  return count;
}
```

### C#

```csharp
public class Solution {
    public int ClosedIsland(int[][] grid) {
        int m = grid.Length;
        int n = grid[0].Length;

        void Dfs(int x, int y) {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 1) return;
            grid[x][y] = 1;
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
                if (grid[i][j] == 0) {
                    count++;
                    Dfs(i, j);
                }
            }
        }
        return count;
    }
}
```

### Java

```java
class Solution {
    public int closedIsland(int[][] grid) {
        int m = grid.length, n = grid[0].length;

        void dfs(int x, int y) {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 1) return;
            grid[x][y] = 1;
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
                if (grid[i][j] == 0) {
                    count++;
                    dfs(i, j);
                }
            }
        }
        return count;
    }
}
```

### Swift

```swift
class Solution {
    func closedIsland(_ grid: [[Int]]) -> Int {
        var grid = grid
        let m = grid.count
        let n = grid[0].count

        func dfs(_ x: Int, _ y: Int) {
            if x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 1 { return }
            grid[x][y] = 1
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
                if grid[i][j] == 0 {
                    count += 1
                    dfs(i, j)
                }
            }
        }
        return count
    }
}
```

### The End