# Shortest Bridge

## Problem Statement

You are given an `n x n` binary matrix `grid` where `1` represents land and `0` represents water. There are exactly two islands in `grid`. You may change `0` to `1` to connect the two islands and form a bridge. Return the smallest number of `0`s you must flip to connect the two islands.

## Input

```text
grid = [[0,1],
        [1,0]]
```

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun shortestBridge(grid: Array<IntArray>): Int {
        val rows = grid.size
        val cols = grid[0].size

        fun dfs(i: Int, j: Int) {
            if (i < 0 || i >= rows || j < 0 || j >= cols || grid[i][j] != 1) return
            grid[i][j] = 2
            dfs(i - 1, j)
            dfs(i + 1, j)
            dfs(i, j - 1)
            dfs(i, j + 1)
        }

        var found = false
        for (i in 0 until rows) {
            if (found) break
            for (j in 0 until cols) {
                if (grid[i][j] == 1) {
                    dfs(i, j)
                    found = true
                    break
                }
            }
        }

        val queue = LinkedList<Pair<Int, Int>>()
        for (i in 0 until rows) {
            for (j in 0 until cols) {
                if (grid[i][j] == 2) {
                    queue.offer(Pair(i, j))
                }
            }
        }

        var steps = 0
        val directions = arrayOf(-1, 0, 1, 0, -1)
        while (queue.isNotEmpty()) {
            val size = queue.size
            for (k in 0 until size) {
                val (x, y) = queue.poll()
                for (d in 0 until 4) {
                    val nx = x + directions[d]
                    val ny = y + directions[d + 1]
                    if (nx < 0 || nx >= rows || ny < 0 || ny >= cols || grid[nx][ny] == 2) continue
                    if (grid[nx][ny] == 1) return steps
                    grid[nx][ny] = 2
                    queue.offer(Pair(nx, ny))
                }
            }
            steps++
        }
        return -1
    }
}
```

### Dart

```dart
int shortestBridge(List<List<int>> grid) {
  final rows = grid.length;
  final cols = grid[0].length;

  void dfs(int i, int j) {
    if (i < 0 || i >= rows || j < 0 || j >= cols || grid[i][j] != 1) return;
    grid[i][j] = 2;
    dfs(i - 1, j);
    dfs(i + 1, j);
    dfs(i, j - 1);
    dfs(i, j + 1);
  }

  bool found = false;
  for (int i = 0; i < rows; i++) {
    if (found) break;
    for (int j = 0; j < cols; j++) {
      if (grid[i][j] == 1) {
        dfs(i, j);
        found = true;
        break;
      }
    }
  }

  final queue = Queue<List<int>>();
  for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
      if (grid[i][j] == 2) {
        queue.add([i, j]);
      }
    }
  }

  int steps = 0;
  final directions = [-1, 0, 1, 0, -1];
  while (queue.isNotEmpty) {
    int size = queue.length;
    for (int k = 0; k < size; k++) {
      final current = queue.removeFirst();
      int x = current[0], y = current[1];
      for (int d = 0; d < 4; d++) {
        int nx = x + directions[d];
        int ny = y + directions[d + 1];
        if (nx < 0 || nx >= rows || ny < 0 || ny >= cols || grid[nx][ny] == 2) continue;
        if (grid[nx][ny] == 1) return steps;
        grid[nx][ny] = 2;
        queue.add([nx, ny]);
      }
    }
    steps++;
  }
  return -1;
}
```

### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public int ShortestBridge(int[][] grid) {
        int rows = grid.Length, cols = grid[0].Length;

        void Dfs(int i, int j) {
            if (i < 0 || i >= rows || j < 0 || j >= cols || grid[i][j] != 1) return;
            grid[i][j] = 2;
            Dfs(i - 1, j);
            Dfs(i + 1, j);
            Dfs(i, j - 1);
            Dfs(i, j + 1);
        }

        bool found = false;
        for (int i = 0; i < rows; i++) {
            if (found) break;
            for (int j = 0; j < cols; j++) {
                if (grid[i][j] == 1) {
                    Dfs(i, j);
                    found = true;
                    break;
                }
            }
        }

        var queue = new Queue<(int, int)>();
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (grid[i][j] == 2) queue.Enqueue((i, j));
            }
        }

        int steps = 0;
        int[] directions = { -1, 0, 1, 0, -1 };
        while (queue.Count > 0) {
            int size = queue.Count;
            for (int k = 0; k < size; k++) {
                var (x, y) = queue.Dequeue();
                for (int d = 0; d < 4; d++) {
                    int nx = x + directions[d], ny = y + directions[d + 1];
                    if (nx < 0 || nx >= rows || ny < 0 || ny >= cols || grid[nx][ny] == 2) continue;
                    if (grid[nx][ny] == 1) return steps;
                    grid[nx][ny] = 2;
                    queue.Enqueue((nx, ny));
                }
            }
            steps++;
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
    public int shortestBridge(int[][] grid) {
        int rows = grid.length, cols = grid[0].length;

        void dfs(int i, int j) {
            if (i < 0 || i >= rows || j < 0 || j >= cols || grid[i][j] != 1) return;
            grid[i][j] = 2;
            dfs(i - 1, j);
            dfs(i + 1, j);
            dfs(i, j - 1);
            dfs(i, j + 1);
        }

        boolean found = false;
        for (int i = 0; i < rows; i++) {
            if (found) break;
            for (int j = 0; j < cols; j++) {
                if (grid[i][j] == 1) {
                    dfs(i, j);
                    found = true;
                    break;
                }
            }
        }

        Queue<int[]> queue = new LinkedList<>();
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (grid[i][j] == 2) queue.offer(new int[]{i, j});
            }
        }

        int steps = 0;
        int[] directions = {-1, 0, 1, 0, -1};
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int k = 0; k < size; k++) {
                int[] current = queue.poll();
                int x = current[0], y = current[1];
                for (int d = 0; d < 4; d++) {
                    int nx = x + directions[d], ny = y + directions[d + 1];
                    if (nx < 0 || nx >= rows || ny < 0 || ny >= cols || grid[nx][ny] == 2) continue;
                    if (grid[nx][ny] == 1) return steps;
                    grid[nx][ny] = 2;
                    queue.offer(new int[]{nx, ny});
                }
            }
            steps++;
        }
        return -1;
    }
}
```

### Swift

```swift
class Solution {
    func shortestBridge(_ grid: [[Int]]) -> Int {
        var grid = grid
        let rows = grid.count
        let cols = grid[0].count

        func dfs(_ i: Int, _ j: Int) {
            guard i >= 0, i < rows, j >= 0, j < cols, grid[i][j] == 1 else { return }
            grid[i][j] = 2
            dfs(i - 1, j)
            dfs(i + 1, j)
            dfs(i, j - 1)
            dfs(i, j + 1)
        }

        var found = false
        for i in 0..<rows {
            if found { break }
            for j in 0..<cols {
                if grid[i][j] == 1 {
                    dfs(i, j)
                    found = true
                    break
                }
            }
        }

        var queue = [(Int, Int)]()
        for i in 0..<rows {
            for j in 0..<cols {
                if grid[i][j] == 2 {
                    queue.append((i, j))
                }
            }
        }

        var steps = 0
        let directions = [-1, 0, 1, 0, -1]
        while !queue.isEmpty {
            let size = queue.count
            for _ in 0..<size {
                let (x, y) = queue.removeFirst()
                for d in 0..<4 {
                    let nx = x + directions[d]
                    let ny = y + directions[d + 1]
                    if nx < 0 || nx >= rows || ny < 0 || ny >= cols || grid[nx][ny] == 2 { continue }
                    if grid[nx][ny] == 1 { return steps }
                    grid[nx][ny] = 2
                    queue.append((nx, ny))
                }
            }
            steps += 1
        }
        return -1
    }
}
```

### The End
