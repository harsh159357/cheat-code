# Game of Life

## Problem Statement

Given a `m x n` board containing 0's (dead) and 1's (alive), implement the Game of Life with the following rules:

1. Any live cell with fewer than two live neighbors dies (under-population).
2. Any live cell with two or three live neighbors survives.
3. Any live cell with more than three live neighbors dies (over-population).
4. Any dead cell with exactly three live neighbors becomes a live cell (reproduction).

## Input

```text
board = [
    [0, 1, 0],
    [0, 0, 1],
    [1, 1, 1],
    [0, 0, 0]
]
```

## Output

```text
[
    [0, 0, 0],
    [1, 0, 1],
    [0, 1, 1],
    [0, 1, 0]
]
```

## Solutions

### Dart

```dart
void gameOfLife(List<List<int>> board) {
  final directions = [
    [-1, -1], [-1, 0], [-1, 1],
    [0, -1],           [0, 1],
    [1, -1], [1, 0], [1, 1]
  ];

  for (var i = 0; i < board.length; i++) {
    for (var j = 0; j < board[0].length; j++) {
      var liveNeighbors = 0;

      for (var dir in directions) {
        var newRow = i + dir[0];
        var newCol = j + dir[1];
        if (newRow >= 0 &&
            newRow < board.length &&
            newCol >= 0 &&
            newCol < board[0].length &&
            (board[newRow][newCol] == 1 || board[newRow][newCol] == -1)) {
          liveNeighbors++;
        }
      }

      if (board[i][j] == 1 && (liveNeighbors < 2 || liveNeighbors > 3)) {
        board[i][j] = -1;
      } else if (board[i][j] == 0 && liveNeighbors == 3) {
        board[i][j] = 2;
      }
    }
  }

  for (var i = 0; i < board.length; i++) {
    for (var j = 0; j < board[0].length; j++) {
      if (board[i][j] == -1) board[i][j] = 0;
      if (board[i][j] == 2) board[i][j] = 1;
    }
  }
}
```

### C#

```csharp
public void GameOfLife(int[][] board) {
    int[][] directions = new int[][] {
        new int[] {-1, -1}, new int[] {-1, 0}, new int[] {-1, 1},
        new int[] {0, -1},                    new int[] {0, 1},
        new int[] {1, -1}, new int[] {1, 0}, new int[] {1, 1}
    };

    int m = board.Length, n = board[0].Length;

    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            int liveNeighbors = 0;
            foreach (var dir in directions) {
                int newRow = i + dir[0], newCol = j + dir[1];
                if (newRow >= 0 && newRow < m && newCol >= 0 && newCol < n &&
                    (board[newRow][newCol] == 1 || board[newRow][newCol] == -1)) {
                    liveNeighbors++;
                }
            }

            if (board[i][j] == 1 && (liveNeighbors < 2 || liveNeighbors > 3)) {
                board[i][j] = -1;
            } else if (board[i][j] == 0 && liveNeighbors == 3) {
                board[i][j] = 2;
            }
        }
    }

    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (board[i][j] == -1) board[i][j] = 0;
            if (board[i][j] == 2) board[i][j] = 1;
        }
    }
}
```

### Java

```java
class Solution {
    public void gameOfLife(int[][] board) {
        int m = board.length, n = board[0].length;
        int[][] directions = {
            {-1, -1}, {-1, 0}, {-1, 1},
            {0, -1},           {0, 1},
            {1, -1}, {1, 0}, {1, 1}
        };

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                int liveNeighbors = 0;
                for (int[] dir : directions) {
                    int newRow = i + dir[0], newCol = j + dir[1];
                    if (newRow >= 0 && newRow < m && newCol >= 0 && newCol < n &&
                        (board[newRow][newCol] == 1 || board[newRow][newCol] == -1)) {
                        liveNeighbors++;
                    }
                }

                if (board[i][j] == 1 && (liveNeighbors < 2 || liveNeighbors > 3)) {
                    board[i][j] = -1;
                } else if (board[i][j] == 0 && liveNeighbors == 3) {
                    board[i][j] = 2;
                }
            }
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (board[i][j] == -1) board[i][j] = 0;
                if (board[i][j] == 2) board[i][j] = 1;
            }
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun gameOfLife(board: Array<IntArray>): Unit {
        val m = board.size
        val n = board[0].size
        val directions = arrayOf(
            intArrayOf(-1, -1), intArrayOf(-1, 0), intArrayOf(-1, 1),
            intArrayOf(0, -1),                    intArrayOf(0, 1),
            intArrayOf(1, -1), intArrayOf(1, 0), intArrayOf(1, 1)
        )

        for (i in 0 until m) {
            for (j in 0 until n) {
                var liveNeighbors = 0
                for (dir in directions) {
                    val newRow = i + dir[0]
                    val newCol = j + dir[1]
                    if (newRow in 0 until m && newCol in 0 until n &&
                        (board[newRow][newCol] == 1 || board[newRow][newCol] == -1)) {
                        liveNeighbors++
                    }
                }

                if (board[i][j] == 1 && (liveNeighbors < 2 || liveNeighbors > 3)) {
                    board[i][j] = -1
                } else if (board[i][j] == 0 && liveNeighbors == 3) {
                    board[i][j] = 2
                }
            }
        }

        for (i in 0 until m) {
            for (j in 0 until n) {
                if (board[i][j] == -1) board[i][j] = 0
                if (board[i][j] == 2) board[i][j] = 1
            }
        }
    }
}
```

### Swift

```swift
class Solution {
    func gameOfLife(_ board: inout [[Int]]) {
        let m = board.count
        let n = board[0].count
        let directions = [
            (-1, -1), (-1, 0), (-1, 1),
            (0, -1),          (0, 1),
            (1, -1), (1, 0), (1, 1)
        ]

        for i in 0..<m {
            for j in 0..<n {
                var liveNeighbors = 0
                for dir in directions {
                    let newRow = i + dir.0
                    let newCol = j + dir.1
                    if newRow >= 0 && newRow < m && newCol >= 0 && newCol < n &&
                        (board[newRow][newCol] == 1 || board[newRow][newCol] == -1) {
                        liveNeighbors += 1
                    }
                }

                if board[i][j] == 1 && (liveNeighbors < 2 || liveNeighbors > 3) {
                    board[i][j] = -1
                } else if board[i][j] == 0 && liveNeighbors == 3 {
                    board[i][j] = 2
                }
            }
        }

        for i in 0..<m {
            for j in 0..<n {
                if board[i][j] == -1 { board[i][j] = 0 }
                if board[i][j] == 2 { board[i][j] = 1 }
            }
        }
    }
}
```

### The End

