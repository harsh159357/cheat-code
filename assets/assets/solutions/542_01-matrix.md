# 01 Matrix

## Problem Statement

Given an `m x n` binary matrix `mat`, return the distance of the nearest `0` for each cell.

The distance between two adjacent cells is `1`.

## Input

```text
matrix = [
    [0, 0, 0],
    [0, 1, 0],
    [1, 1, 1]
]
```

## Output

```text
[
    [0, 0, 0],
    [0, 1, 0],
    [1, 2, 1]
]
```

## Solutions

### Dart

```dart
List<List<int>> updateMatrix(List<List<int>> mat) {
  int rows = mat.length;
  int cols = mat[0].length;
  Queue<List<int>> queue = Queue();

  for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
      if (mat[i][j] == 0) {
        queue.add([i, j]);
      } else {
        mat[i][j] = 10000;
      }
    }
  }

  List<List<int>> directions = [
    [-1, 0],
    [1, 0],
    [0, -1],
    [0, 1]
  ];

  while (queue.isNotEmpty) {
    List<int> cell = queue.removeFirst();
    int x = cell[0];
    int y = cell[1];

    for (List<int> dir in directions) {
      int newX = x + dir[0];
      int newY = y + dir[1];
      if (newX >= 0 && newX < rows && newY >= 0 && newY < cols) {
        if (mat[x][y] + 1 < mat[newX][newY]) {
          mat[newX][newY] = mat[x][y] + 1;
          queue.add([newX, newY]);
        }
      }
    }
  }

  return mat;
}
```

### C#

```csharp
public class Solution {
    public int[][] UpdateMatrix(int[][] mat) {
        int rows = mat.Length;
        int cols = mat[0].Length;
        Queue<(int, int)> queue = new Queue<(int, int)>();

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (mat[i][j] == 0) {
                    queue.Enqueue((i, j));
                } else {
                    mat[i][j] = int.MaxValue;
                }
            }
        }

        int[][] directions = new int[][] {
            new int[] { -1, 0 }, new int[] { 1, 0 },
            new int[] { 0, -1 }, new int[] { 0, 1 }
        };

        while (queue.Count > 0) {
            var (x, y) = queue.Dequeue();
            foreach (var dir in directions) {
                int newX = x + dir[0];
                int newY = y + dir[1];
                if (newX >= 0 && newX < rows && newY >= 0 && newY < cols) {
                    if (mat[x][y] + 1 < mat[newX][newY]) {
                        mat[newX][newY] = mat[x][y] + 1;
                        queue.Enqueue((newX, newY));
                    }
                }
            }
        }

        return mat;
    }
}
```

### Java

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int[][] updateMatrix(int[][] mat) {
        int rows = mat.length;
        int cols = mat[0].length;
        Queue<int[]> queue = new LinkedList<>();

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (mat[i][j] == 0) {
                    queue.offer(new int[]{i, j});
                } else {
                    mat[i][j] = Integer.MAX_VALUE;
                }
            }
        }

        int[][] directions = {
            {-1, 0}, {1, 0}, {0, -1}, {0, 1}
        };

        while (!queue.isEmpty()) {
            int[] cell = queue.poll();
            int x = cell[0], y = cell[1];
            for (int[] dir : directions) {
                int newX = x + dir[0];
                int newY = y + dir[1];
                if (newX >= 0 && newX < rows && newY >= 0 && newY < cols) {
                    if (mat[x][y] + 1 < mat[newX][newY]) {
                        mat[newX][newY] = mat[x][y] + 1;
                        queue.offer(new int[]{newX, newY});
                    }
                }
            }
        }

        return mat;
    }
}
```

### Kotlin

```kotlin
import java.util.LinkedList

class Solution {
    fun updateMatrix(matrix: Array<IntArray>): Array<IntArray> {
        val rows = matrix.size
        val cols = matrix[0].size
        val queue = LinkedList<Pair<Int, Int>>()

        for (i in 0 until rows) {
            for (j in 0 until cols) {
                if (matrix[i][j] == 0) {
                    queue.offer(Pair(i, j))
                } else {
                    matrix[i][j] = Int.MAX_VALUE
                }
            }
        }

        val directions = arrayOf(
            intArrayOf(-1, 0), intArrayOf(1, 0),
            intArrayOf(0, -1), intArrayOf(0, 1)
        )

        while (queue.isNotEmpty()) {
            val (x, y) = queue.poll()
            for (dir in directions) {
                val newX = x + dir[0]
                val newY = y + dir[1]
                if (newX in 0 until rows && newY in 0 until cols) {
                    if (matrix[x][y] + 1 < matrix[newX][newY]) {
                        matrix[newX][newY] = matrix[x][y] + 1
                        queue.offer(Pair(newX, newY))
                    }
                }
            }
        }

        return matrix
    }
}
```

### Swift

```swift
class Solution {
    func updateMatrix(_ mat: [[Int]]) -> [[Int]] {
        var mat = mat
        let rows = mat.count
        let cols = mat[0].count
        var queue = [(Int, Int)]()

        for i in 0..<rows {
            for j in 0..<cols {
                if mat[i][j] == 0 {
                    queue.append((i, j))
                } else {
                    mat[i][j] = Int.max
                }
            }
        }

        let directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]

        while !queue.isEmpty {
            let (x, y) = queue.removeFirst()
            for dir in directions {
                let newX = x + dir.0
                let newY = y + dir.1
                if newX >= 0 && newX < rows && newY >= 0 && newY < cols {
                    if mat[x][y] + 1 < mat[newX][newY] {
                        mat[newX][newY] = mat[x][y] + 1
                        queue.append((newX, newY))
                    }
                }
            }
        }

        return mat
    }
}
```

### The End