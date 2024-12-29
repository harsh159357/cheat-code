# Max Area of Island

## Problem Statement

You are given an `m x n` binary grid `grid` where `1` represents land and `0` represents water. An island is a group of `1`s connected 4-directionally (horizontal or vertical). You may assume all four edges of the grid are surrounded by water.

The area of an island is the number of cells with a value `1` in the island.

Return the maximum area of an island in the grid. If there is no island, return `0`.

## Input

```text
grid = [
    [1, 1, 0, 0, 0],
    [1, 1, 0, 0, 0],
    [0, 0, 0, 1, 1],
    [0, 0, 0, 1, 1]
]
```

## Output

```text
4
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxAreaOfIsland(grid: Array<IntArray>): Int {
        val m = grid.size
        val n = grid[0].size
        var maxArea = 0

        // Perform DFS to calculate area of each island
        fun dfs(x: Int, y: Int): Int {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 0) {
                return 0
            }
            grid[x][y] = 0 // Mark as visited
            var area = 1 // Current cell contributes to the area
            // Explore adjacent cells
            area += dfs(x + 1, y)
            area += dfs(x - 1, y)
            area += dfs(x, y + 1)
            area += dfs(x, y - 1)
            return area
        }

        // Iterate through the grid to find the maximum area
        for (i in 0 until m) {
            for (j in 0 until n) {
                if (grid[i][j] == 1) {
                    maxArea = maxOf(maxArea, dfs(i, j))
                }
            }
        }

        return maxArea
    }
}

fun main() {
    val solution = Solution()
    val grid = arrayOf(
        intArrayOf(1, 1, 0, 0, 0),
        intArrayOf(1, 1, 0, 0, 0),
        intArrayOf(0, 0, 0, 1, 1),
        intArrayOf(0, 0, 0, 1, 1)
    )
    println("Maximum area of island: ${solution.maxAreaOfIsland(grid)}") // Output: 4
}
```


### Dart

```dart
int maxAreaOfIsland(List<List<int>> grid) {
  int m = grid.length;
  int n = grid[0].length;
  int maxArea = 0;

  int dfs(int x, int y) {
    if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 0) {
      return 0;
    }
    grid[x][y] = 0; // Mark as visited
    int area = 1;
    area += dfs(x + 1, y);
    area += dfs(x - 1, y);
    area += dfs(x, y + 1);
    area += dfs(x, y - 1);
    return area;
  }

  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (grid[i][j] == 1) {
        maxArea = max(maxArea, dfs(i, j));
      }
    }
  }

  return maxArea;
}

void main() {
  List<List<int>> grid = [
    [1, 1, 0, 0, 0],
    [1, 1, 0, 0, 0],
    [0, 0, 0, 1, 1],
    [0, 0, 0, 1, 1]
  ];
  print("Maximum area of island: ${maxAreaOfIsland(grid)}"); // Output: 4
}
```


### C#

```csharp
public class Solution {
    public int MaxAreaOfIsland(int[][] grid) {
        int m = grid.Length, n = grid[0].Length;
        int maxArea = 0;

        int Dfs(int x, int y) {
            if (x < 0 || x >= m || y < 0 || y >= n || grid[x][y] == 0) {
                return 0;
            }
            grid[x][y] = 0; // Mark as visited
            int area = 1;
            area += Dfs(x + 1, y);
            area += Dfs(x - 1, y);
            area += Dfs(x, y + 1);
            area += Dfs(x, y - 1);
            return area;
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1) {
                    maxArea = Math.Max(maxArea, Dfs(i, j));
                }
            }
        }

        return maxArea;
    }
}
```


### The End