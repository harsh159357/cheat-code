# Shortest Path in Binary Matrix

## Problem Statement

Given an `n x n` binary matrix `grid`, return the length of the shortest clear path from the top-left corner to the bottom-right corner. If no such path exists, return `-1`.

A clear path in a binary matrix is a path from top-left to bottom-right such that all the visited cells are `0`. A path is defined as a sequence of cells where adjacent cells share an edge or a corner.

## Input

```text
grid = [
    [0, 0, 0],
    [1, 1, 0],
    [1, 1, 0]
]
```

## Output

```text
Length of the shortest path: 4
```

## Solutions

### Kotlin

```kotlin
import java.util.LinkedList

class Solution {
    fun shortestPathBinaryMatrix(grid: Array<IntArray>): Int {
        val n = grid.size
        if (grid[0][0] == 1 || grid[n - 1][n - 1] == 1) {
            return -1 // No valid path exists
        }

        val directions = arrayOf(
            intArrayOf(-1, -1), intArrayOf(-1, 0), intArrayOf(-1, 1),
            intArrayOf(0, -1), intArrayOf(0, 1),
            intArrayOf(1, -1), intArrayOf(1, 0), intArrayOf(1, 1)
        )

        val queue = LinkedList<Pair<Int, Int>>()
        queue.offer(Pair(0, 0))
        grid[0][0] = 1 // Mark the start cell as visited and set its distance to 1

        while (queue.isNotEmpty()) {
            val (x, y) = queue.poll()

            if (x == n - 1 && y == n - 1) {
                return grid[x][y] // Return the distance of the bottom-right corner
            }

            for (dir in directions) {
                val newX = x + dir[0]
                val newY = y + dir[1]

                // Check if the new coordinates are within bounds and the cell is not blocked
                if (newX in 0 until n && newY in 0 until n && grid[newX][newY] == 0) {
                    grid[newX][newY] = grid[x][y] + 1 // Update the distance
                    queue.offer(Pair(newX, newY))
                }
            }
        }

        return -1 // No valid path exists
    }
}
```

### Dart

```dart
int shortestPathBinaryMatrix(List<List<int>> grid) {
  final int n = grid.length;
  if (grid[0][0] == 1 || grid[n - 1][n - 1] == 1) return -1;

  final directions = [
    [-1, -1], [-1, 0], [-1, 1],
    [0, -1], [0, 1],
    [1, -1], [1, 0], [1, 1]
  ];

  final queue = Queue<List<int>>();
  queue.add([0, 0]);
  grid[0][0] = 1;

  while (queue.isNotEmpty) {
    final current = queue.removeFirst();
    final x = current[0], y = current[1];

    if (x == n - 1 && y == n - 1) return grid[x][y];

    for (final dir in directions) {
      final newX = x + dir[0], newY = y + dir[1];

      if (newX >= 0 && newX < n && newY >= 0 && newY < n && grid[newX][newY] == 0) {
        grid[newX][newY] = grid[x][y] + 1;
        queue.add([newX, newY]);
      }
    }
  }

  return -1;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public int ShortestPathBinaryMatrix(int[][] grid) {
        int n = grid.Length;
        if (grid[0][0] == 1 || grid[n - 1][n - 1] == 1) return -1;

        int[][] directions = new int[][] {
            new int[] {-1, -1}, new int[] {-1, 0}, new int[] {-1, 1},
            new int[] {0, -1}, new int[] {0, 1},
            new int[] {1, -1}, new int[] {1, 0}, new int[] {1, 1}
        };

        Queue<(int, int)> queue = new Queue<(int, int)>();
        queue.Enqueue((0, 0));
        grid[0][0] = 1;

        while (queue.Count > 0) {
            var (x, y) = queue.Dequeue();

            if (x == n - 1 && y == n - 1) return grid[x][y];

            foreach (var dir in directions) {
                int newX = x + dir[0], newY = y + dir[1];
                if (newX >= 0 && newX < n && newY >= 0 && newY < n && grid[newX][newY] == 0) {
                    grid[newX][newY] = grid[x][y] + 1;
                    queue.Enqueue((newX, newY));
                }
            }
        }

        return -1;
    }
}
```

### Java

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int shortestPathBinaryMatrix(int[][] grid) {
        int n = grid.length;
        if (grid[0][0] == 1 || grid[n - 1][n - 1] == 1) return -1;

        int[][] directions = {
            {-1, -1}, {-1, 0}, {-1, 1},
            {0, -1}, {0, 1},
            {1, -1}, {1, 0}, {1, 1}
        };

        Queue<int[]> queue = new LinkedList<>();
        queue.add(new int[]{0, 0});
        grid[0][0] = 1;

        while (!queue.isEmpty()) {
            int[] current = queue.poll();
            int x = current[0], y = current[1];

            if (x == n - 1 && y == n - 1) return grid[x][y];

            for (int[] dir : directions) {
                int newX = x + dir[0], newY = y + dir[1];
                if (newX >= 0 && newX < n && newY >= 0 && newY < n && grid[newX][newY] == 0) {
                    grid[newX][newY] = grid[x][y] + 1;
                    queue.add(new int[]{newX, newY});
                }
            }
        }

        return -1;
    }
}
```

### The End