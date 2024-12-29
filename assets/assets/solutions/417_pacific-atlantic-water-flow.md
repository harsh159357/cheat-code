# Pacific Atlantic Water Flow

## Problem Statement

Given an `m x n` matrix of non-negative integers representing the height of each cell, return a list of grid coordinates where water can flow to both the Pacific and Atlantic oceans. Water can flow from a cell to another adjacent cell with an equal or lower height.

The Pacific ocean touches the left and top edges, and the Atlantic ocean touches the right and bottom edges.

## Input

```text
matrix = [
    [1, 2, 2, 3, 5],
    [3, 2, 3, 4, 4],
    [2, 4, 5, 3, 1],
    [6, 7, 1, 4, 5],
    [5, 1, 1, 2, 4]
]
```

## Output

```text
[[0, 4], [1, 3], [1, 4], [2, 2], [3, 0], [3, 1], [4, 0]]
```

## Solutions

### Dart

```dart
List<List<int>> pacificAtlantic(List<List<int>> matrix) {
  if (matrix.isEmpty || matrix[0].isEmpty) return [];

  int m = matrix.length;
  int n = matrix[0].length;
  List<List<bool>> pacific = List.generate(m, (_) => List.filled(n, false));
  List<List<bool>> atlantic = List.generate(m, (_) => List.filled(n, false));
  List<List<int>> result = [];

  void dfs(int x, int y, List<List<bool>> ocean) {
    ocean[x][y] = true;
    List<int> directions = [0, 1, 0, -1, 0];
    for (int i = 0; i < 4; i++) {
      int nx = x + directions[i];
      int ny = y + directions[i + 1];
      if (nx >= 0 &&
          nx < m &&
          ny >= 0 &&
          ny < n &&
          !ocean[nx][ny] &&
          matrix[nx][ny] >= matrix[x][y]) {
        dfs(nx, ny, ocean);
      }
    }
  }

  // Perform DFS for the Pacific and Atlantic borders
  for (int i = 0; i < m; i++) {
    dfs(i, 0, pacific);
    dfs(i, n - 1, atlantic);
  }
  for (int j = 0; j < n; j++) {
    dfs(0, j, pacific);
    dfs(m - 1, j, atlantic);
  }

  // Collect cells reachable by both oceans
  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (pacific[i][j] && atlantic[i][j]) {
        result.add([i, j]);
      }
    }
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public IList<IList<int>> PacificAtlantic(int[][] matrix) {
        if (matrix.Length == 0 || matrix[0].Length == 0) return new List<IList<int>>();

        int m = matrix.Length, n = matrix[0].Length;
        bool[,] pacific = new bool[m, n];
        bool[,] atlantic = new bool[m, n];
        var result = new List<IList<int>>();

        void Dfs(int x, int y, bool[,] ocean) {
            ocean[x, y] = true;
            int[] directions = { 0, 1, 0, -1, 0 };
            for (int i = 0; i < 4; i++) {
                int nx = x + directions[i];
                int ny = y + directions[i + 1];
                if (nx >= 0 && nx < m && ny >= 0 && ny < n && 
                    !ocean[nx, ny] && matrix[nx][ny] >= matrix[x][y]) {
                    Dfs(nx, ny, ocean);
                }
            }
        }

        for (int i = 0; i < m; i++) {
            Dfs(i, 0, pacific);
            Dfs(i, n - 1, atlantic);
        }
        for (int j = 0; j < n; j++) {
            Dfs(0, j, pacific);
            Dfs(m - 1, j, atlantic);
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (pacific[i, j] && atlantic[i, j]) {
                    result.Add(new List<int> { i, j });
                }
            }
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public List<List<Integer>> pacificAtlantic(int[][] matrix) {
        if (matrix.length == 0 || matrix[0].length == 0) return new ArrayList<>();

        int m = matrix.length, n = matrix[0].length;
        boolean[][] pacific = new boolean[m][n];
        boolean[][] atlantic = new boolean[m][n];
        List<List<Integer>> result = new ArrayList<>();

        int[] directions = {0, 1, 0, -1, 0};

        void dfs(int x, int y, boolean[][] ocean) {
            ocean[x][y] = true;
            for (int i = 0; i < 4; i++) {
                int nx = x + directions[i], ny = y + directions[i + 1];
                if (nx >= 0 && nx < m && ny >= 0 && ny < n && 
                    !ocean[nx][ny] && matrix[nx][ny] >= matrix[x][y]) {
                    dfs(nx, ny, ocean);
                }
            }
        }

        for (int i = 0; i < m; i++) {
            dfs(i, 0, pacific);
            dfs(i, n - 1, atlantic);
        }
        for (int j = 0; j < n; j++) {
            dfs(0, j, pacific);
            dfs(m - 1, j, atlantic);
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (pacific[i][j] && atlantic[i][j]) {
                    result.add(Arrays.asList(i, j));
                }
            }
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun pacificAtlantic(matrix: Array<IntArray>): List<List<Int>> {
        if (matrix.isEmpty() || matrix[0].isEmpty()) return emptyList()

        val m = matrix.size
        val n = matrix[0].size
        val pacific = Array(m) { BooleanArray(n) }
        val atlantic = Array(m) { BooleanArray(n) }
        val result = mutableListOf<List<Int>>()

        fun dfs(x: Int, y: Int, ocean: Array<BooleanArray>) {
            ocean[x][y] = true
            val directions = arrayOf(0, 1, 0, -1, 0)
            for (i in 0 until 4) {
                val nx = x + directions[i]
                val ny = y + directions[i + 1]
                if (nx in 0 until m && ny in 0 until n && !ocean[nx][ny] && matrix[nx][ny] >= matrix[x][y]) {
                    dfs(nx, ny, ocean)
                }
            }
        }

        for (i in 0 until m) {
            dfs(i, 0, pacific)
            dfs(i, n - 1, atlantic)
        }
        for (j in 0 until n) {
            dfs(0, j, pacific)
            dfs(m - 1, j, atlantic)
        }

        for (i in 0 until m) {
            for (j in 0 until n) {
                if (pacific[i][j] && atlantic[i][j]) {
                    result.add(listOf(i, j))
                }
            }
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func pacificAtlantic(_ matrix: [[Int]]) -> [[Int]] {
        if matrix.isEmpty || matrix[0].isEmpty { return [] }

        let m = matrix.count, n = matrix[0].count
        var pacific = Array(repeating: Array(repeating: false, count: n), count: m)
        var atlantic = Array(repeating: Array(repeating: false, count: n), count: m)
        var result: [[Int]] = []

        let directions = [(0, 1), (1, 0), (0, -1), (-1, 0)]

        func dfs(_ x: Int, _ y: Int, _ ocean: inout [[Bool]]) {
            ocean[x][y] = true
            for (dx, dy) in directions {
                let nx = x + dx, ny = y + dy
                if nx >= 0 && nx < m && ny >= 0 && ny < n && 
                    !ocean[nx][ny] && matrix[nx][ny] >= matrix[x][y] {
                    dfs(nx, ny, &ocean)
                }
            }
        }

        for i in 0..<m {
            dfs(i, 0, &pacific)
            dfs(i, n - 1, &atlantic)
        }
        for j in 0..<n {
            dfs(0, j, &pacific)
            dfs(m - 1, j, &atlantic)
        }

        for i in 0..<m {
            for j in 0..<n {
                if pacific[i][j] && atlantic[i][j] {
                    result.append([i, j])
                }
            }
        }

        return result
    }
}
```

### The End