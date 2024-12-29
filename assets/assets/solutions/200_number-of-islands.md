# Number of Islands

## Problem Statement

Given a 2D grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. Assume all four edges of the grid are surrounded by water.

## Input

```text
grid = [
  ['1', '1', '0', '0', '0'],
  ['1', '1', '0', '0', '0'],
  ['0', '0', '1', '0', '0'],
  ['0', '0', '0', '1', '1']
]
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int numIslands(List<List<String>> grid) {
  if (grid.isEmpty || grid[0].isEmpty) return 0;

  int rows = grid.length;
  int cols = grid[0].length;
  int islands = 0;

  void dfs(int row, int col) {
    if (row < 0 || col < 0 || row >= rows || col >= cols || grid[row][col] == '0') return;
    grid[row][col] = '0';
    dfs(row + 1, col);
    dfs(row - 1, col);
    dfs(row, col + 1);
    dfs(row, col - 1);
  }

  for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
      if (grid[i][j] == '1') {
        islands++;
        dfs(i, j);
      }
    }
  }

  return islands;
}
```

### C#

```csharp
public class Solution {
    public int NumIslands(char[][] grid) {
        if (grid.Length == 0 || grid[0].Length == 0) return 0;

        int rows = grid.Length;
        int cols = grid[0].Length;
        int islands = 0;

        void Dfs(int row, int col) {
            if (row < 0 || col < 0 || row >= rows || col >= cols || grid[row][col] == '0') return;
            grid[row][col] = '0';
            Dfs(row + 1, col);
            Dfs(row - 1, col);
            Dfs(row, col + 1);
            Dfs(row, col - 1);
        }

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (grid[i][j] == '1') {
                    islands++;
                    Dfs(i, j);
                }
            }
        }

        return islands;
    }
}
```

### Java

```java
class Solution {
    public int numIslands(char[][] grid) {
        if (grid == null || grid.length == 0) return 0;

        int rows = grid.length;
        int cols = grid[0].length;
        int islands = 0;

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (grid[i][j] == '1') {
                    islands++;
                    dfs(grid, i, j);
                }
            }
        }

        return islands;
    }

    private void dfs(char[][] grid, int row, int col) {
        if (row < 0 || col < 0 || row >= grid.length || col >= grid[0].length || grid[row][col] == '0') return;
        grid[row][col] = '0';
        dfs(grid, row + 1, col);
        dfs(grid, row - 1, col);
        dfs(grid, row, col + 1);
        dfs(grid, row, col - 1);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun numIslands(grid: Array<CharArray>): Int {
        if (grid.isEmpty() || grid[0].isEmpty()) return 0

        val rows = grid.size
        val cols = grid[0].size
        var islands = 0

        fun dfs(row: Int, col: Int) {
            if (row < 0 || col < 0 || row >= rows || col >= cols || grid[row][col] == '0') return
            grid[row][col] = '0'
            dfs(row + 1, col)
            dfs(row - 1, col)
            dfs(row, col + 1)
            dfs(row, col - 1)
        }

        for (i in 0 until rows) {
            for (j in 0 until cols) {
                if (grid[i][j] == '1') {
                    islands++
                    dfs(i, j)
                }
            }
        }
        return islands
    }
}
```

### Swift

```swift
class Solution {
    func numIslands(_ grid: [[Character]]) -> Int {
        if grid.isEmpty || grid[0].isEmpty { return 0 }

        let rows = grid.count
        let cols = grid[0].count
        var grid = grid
        var islands = 0

        func dfs(_ row: Int, _ col: Int) {
            if row < 0 || col < 0 || row >= rows || col >= cols || grid[row][col] == "0" { return }
            grid[row][col] = "0"
            dfs(row + 1, col)
            dfs(row - 1, col)
            dfs(row, col + 1)
            dfs(row, col - 1)
        }

        for i in 0..<rows {
            for j in 0..<cols {
                if grid[i][j] == "1" {
                    islands += 1
                    dfs(i, j)
                }
            }
        }

        return islands
    }
}
```


### The End

