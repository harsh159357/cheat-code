# Surrounded Regions

## Problem Statement

Given an `m x n` matrix `board` containing `'X'` and `'O'`, capture all regions surrounded by `'X'`.

A region is captured by flipping all `'O'`s into `'X'`s in that surrounded region.

---

## Input

```text
board = [
  ["X", "X", "X", "X"],
  ["X", "O", "O", "X"],
  ["X", "X", "O", "X"],
  ["X", "O", "X", "X"]
]
```

## Output

```text
[
  ["X", "X", "X", "X"],
  ["X", "X", "X", "X"],
  ["X", "X", "X", "X"],
  ["X", "O", "X", "X"]
]
```


## Solutions

### Dart

```dart
void solve(List<List<String>> board) {
  void dfs(int row, int col) {
    if (row < 0 || col < 0 || row >= board.length || col >= board[0].length || board[row][col] != 'O') {
      return;
    }
    board[row][col] = 'Y';
    dfs(row + 1, col);
    dfs(row - 1, col);
    dfs(row, col + 1);
    dfs(row, col - 1);
  }

  int rows = board.length;
  int cols = board[0].length;

  // Mark 'O' connected to boundaries as 'Y'
  for (int i = 0; i < rows; i++) {
    dfs(i, 0);
    dfs(i, cols - 1);
  }
  for (int j = 0; j < cols; j++) {
    dfs(0, j);
    dfs(rows - 1, j);
  }

  // Convert remaining 'O' to 'X', and revert 'Y' to 'O'
  for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
      if (board[i][j] == 'O') board[i][j] = 'X';
      else if (board[i][j] == 'Y') board[i][j] = 'O';
    }
  }
}
```


### C#

```csharp
public class Solution {
    public void Solve(char[][] board) {
        void DFS(int row, int col) {
            if (row < 0 || col < 0 || row >= board.Length || col >= board[0].Length || board[row][col] != 'O') {
                return;
            }
            board[row][col] = 'Y';
            DFS(row + 1, col);
            DFS(row - 1, col);
            DFS(row, col + 1);
            DFS(row, col - 1);
        }

        int rows = board.Length;
        int cols = board[0].Length;

        // Mark 'O' connected to boundaries as 'Y'
        for (int i = 0; i < rows; i++) {
            DFS(i, 0);
            DFS(i, cols - 1);
        }
        for (int j = 0; j < cols; j++) {
            DFS(0, j);
            DFS(rows - 1, j);
        }

        // Convert remaining 'O' to 'X', and revert 'Y' to 'O'
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (board[i][j] == 'O') board[i][j] = 'X';
                else if (board[i][j] == 'Y') board[i][j] = 'O';
            }
        }
    }
}
```


### Java

```java
class Solution {
    public void solve(char[][] board) {
        int rows = board.length;
        int cols = board[0].length;

        // Mark 'O' connected to boundaries as 'Y'
        for (int i = 0; i < rows; i++) {
            dfs(board, i, 0);
            dfs(board, i, cols - 1);
        }
        for (int j = 0; j < cols; j++) {
            dfs(board, 0, j);
            dfs(board, rows - 1, j);
        }

        // Convert remaining 'O' to 'X', and revert 'Y' to 'O'
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (board[i][j] == 'O') board[i][j] = 'X';
                else if (board[i][j] == 'Y') board[i][j] = 'O';
            }
        }
    }

    private void dfs(char[][] board, int row, int col) {
        if (row < 0 || col < 0 || row >= board.length || col >= board[0].length || board[row][col] != 'O') {
            return;
        }
        board[row][col] = 'Y';
        dfs(board, row + 1, col);
        dfs(board, row - 1, col);
        dfs(board, row, col + 1);
        dfs(board, row, col - 1);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun solve(board: Array<CharArray>) {
        fun dfs(row: Int, col: Int) {
            if (row < 0 || col < 0 || row >= board.size || col >= board[0].size || board[row][col] != 'O') return
            board[row][col] = 'Y'
            dfs(row + 1, col)
            dfs(row - 1, col)
            dfs(row, col + 1)
            dfs(row, col - 1)
        }

        val rows = board.size
        val cols = board[0].size

        // Mark 'O' connected to boundaries as 'Y'
        for (i in 0 until rows) {
            dfs(i, 0)
            dfs(i, cols - 1)
        }
        for (j in 0 until cols) {
            dfs(0, j)
            dfs(rows - 1, j)
        }

        // Convert remaining 'O' to 'X', and revert 'Y' to 'O'
        for (i in 0 until rows) {
            for (j in 0 until cols) {
                if (board[i][j] == 'O') board[i][j] = 'X'
                else if (board[i][j] == 'Y') board[i][j] = 'O'
            }
        }
    }
}
```


### Swift

```swift
class Solution {
    func solve(_ board: inout [[Character]]) {
        let rows = board.count
        let cols = board[0].count

        func dfs(_ row: Int, _ col: Int) {
            if row < 0 || col < 0 || row >= rows || col >= cols || board[row][col] != "O" { return }
            board[row][col] = "Y"
            dfs(row + 1, col)
            dfs(row - 1, col)
            dfs(row, col + 1)
            dfs(row, col - 1)
        }

        // Mark 'O' connected to boundaries as 'Y'
        for i in 0..<rows {
            dfs(i, 0)
            dfs(i, cols - 1)
        }
        for j in 0..<cols {
            dfs(0, j)
            dfs(rows - 1, j)
        }

        // Convert remaining 'O' to 'X', and revert 'Y' to 'O'
        for i in 0..<rows {
            for j in 0..<cols {
                if board[i][j] == "O" {
                    board[i][j] = "X"
                } else if board[i][j] == "Y" {
                    board[i][j] = "O"
                }
            }
        }
    }
}
```


### The End

