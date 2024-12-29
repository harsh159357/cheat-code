# Rotting Oranges

## Problem Statement

You are given an `m x n` grid where:

- `0` represents an empty cell,
- `1` represents a fresh orange, and
- `2` represents a rotten orange.

Every minute, any fresh orange that is adjacent (4-directionally) to a rotten orange becomes rotten. Return the minimum number of minutes that must elapse until no cell has a fresh orange. If it is impossible to rot every fresh orange, return `-1`.

## Input

```text
grid = [[2,1,1],[1,1,0],[0,1,1]]
```

## Output

```text
4
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun orangesRotting(grid: Array<IntArray>): Int {
        val directions = arrayOf(-1, 0, 1, 0, -1)
        val m = grid.size
        val n = grid[0].size
        var freshCount = 0
        val queue = LinkedList<IntArray>()

        for (i in 0 until m) {
            for (j in 0 until n) {
                if (grid[i][j] == 2) {
                    queue.offer(intArrayOf(i, j))
                } else if (grid[i][j] == 1) {
                    freshCount++
                }
            }
        }

        var minutes = 0
        while (queue.isNotEmpty() && freshCount > 0) {
            val size = queue.size
            for (i in 0 until size) {
                val (x, y) = queue.poll()
                for (d in 0 until 4) {
                    val nx = x + directions[d]
                    val ny = y + directions[d + 1]
                    if (nx in 0 until m && ny in 0 until n && grid[nx][ny] == 1) {
                        grid[nx][ny] = 2
                        queue.offer(intArrayOf(nx, ny))
                        freshCount--
                    }
                }
            }
            minutes++
        }

        return if (freshCount == 0) minutes else -1
    }
}
```

### Dart

```dart
int orangesRotting(List<List<int>> grid) {
  final directions = [-1, 0, 1, 0, -1];
  final m = grid.length;
  final n = grid[0].length;
  int freshCount = 0;
  final queue = Queue<List<int>>();

  for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
      if (grid[i][j] == 2) {
        queue.add([i, j]);
      } else if (grid[i][j] == 1) {
        freshCount++;
      }
    }
  }

  int minutes = 0;
  while (queue.isNotEmpty && freshCount > 0) {
    final size = queue.length;
    for (int i = 0; i < size; i++) {
      final current = queue.removeFirst();
      final x = current[0], y = current[1];
      for (int d = 0; d < 4; d++) {
        final nx = x + directions[d];
        final ny = y + directions[d + 1];
        if (nx >= 0 && nx < m && ny >= 0 && ny < n && grid[nx][ny] == 1) {
          grid[nx][ny] = 2;
          queue.add([nx, ny]);
          freshCount--;
        }
      }
    }
    minutes++;
  }

  return freshCount == 0 ? minutes : -1;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public int OrangesRotting(int[][] grid) {
        int[] directions = { -1, 0, 1, 0, -1 };
        int m = grid.Length, n = grid[0].Length;
        int freshCount = 0;
        Queue<int[]> queue = new Queue<int[]>();

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 2) {
                    queue.Enqueue(new int[] { i, j });
                } else if (grid[i][j] == 1) {
                    freshCount++;
                }
            }
        }

        int minutes = 0;
        while (queue.Count > 0 && freshCount > 0) {
            int size = queue.Count;
            for (int i = 0; i < size; i++) {
                int[] current = queue.Dequeue();
                int x = current[0], y = current[1];
                for (int d = 0; d < 4; d++) {
                    int nx = x + directions[d];
                    int ny = y + directions[d + 1];
                    if (nx >= 0 && nx < m && ny >= 0 && ny < n && grid[nx][ny] == 1) {
                        grid[nx][ny] = 2;
                        queue.Enqueue(new int[] { nx, ny });
                        freshCount--;
                    }
                }
            }
            minutes++;
        }

        return freshCount == 0 ? minutes : -1;
    }
}
```

### Java

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int orangesRotting(int[][] grid) {
        int[] directions = { -1, 0, 1, 0, -1 };
        int m = grid.length, n = grid[0].length;
        int freshCount = 0;
        Queue<int[]> queue = new LinkedList<>();

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 2) {
                    queue.add(new int[] { i, j });
                } else if (grid[i][j] == 1) {
                    freshCount++;
                }
            }
        }

        int minutes = 0;
        while (!queue.isEmpty() && freshCount > 0) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                int[] current = queue.poll();
                int x = current[0], y = current[1];
                for (int d = 0; d < 4; d++) {
                    int nx = x + directions[d];
                    int ny = y + directions[d + 1];
                    if (nx >= 0 && nx < m && ny >= 0 && ny < n && grid[nx][ny] == 1) {
                        grid[nx][ny] = 2;
                        queue.add(new int[] { nx, ny });
                        freshCount--;
                    }
                }
            }
            minutes++;
        }

        return freshCount == 0 ? minutes : -1;
    }
}
```

### Swift

```swift
class Solution {
    func orangesRotting(_ grid: [[Int]]) -> Int {
        var grid = grid
        let directions = [-1, 0, 1, 0, -1]
        let m = grid.count
        let n = grid[0].count
        var freshCount = 0
        var queue = [(Int, Int)]()

        for i in 0..<m {
            for j in 0..<n {
                if grid[i][j] == 2 {
                    queue.append((i, j))
                } else if grid[i][j] == 1 {
                    freshCount += 1
                }
            }
        }

        var minutes = 0
        while !queue.isEmpty && freshCount > 0 {
            let size = queue.count
            for _ in 0..<size {
                let (x, y) = queue.removeFirst()
                for d in 0..<4 {
                    let nx = x + directions[d]
                    let ny = y + directions[d + 1]
                    if nx >= 0 && nx < m && ny >= 0 && ny < n && grid[nx][ny] == 1 {
                        grid[nx][ny] = 2
                        queue.append((nx, ny))
                        freshCount -= 1
                    }
                }
            }
            minutes += 1
        }

        return freshCount == 0 ? minutes : -1
    }
}
```

### The End