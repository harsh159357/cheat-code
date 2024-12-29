# Word Search

## Problem Statement

Given an `m x n` grid of characters `board` and a string `word`, return `true` if `word` exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where "adjacent" cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

## Input

```text
board = [
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]
word = "ABCCED"
```

## Output

```text
true
```

(Explanation: The word "ABCCED" can be found in the board following adjacent cells.)

## Solutions

### Dart

```dart
bool exist(List<List<String>> board, String word) {
  int rows = board.length;
  int cols = board[0].length;

  bool dfs(int row, int col, int index) {
    if (index == word.length) return true;
    if (row < 0 || row >= rows || col < 0 || col >= cols || board[row][col] != word[index]) return false;

    String temp = board[row][col];
    board[row][col] = '#';
    bool found = dfs(row - 1, col, index + 1) ||
                 dfs(row + 1, col, index + 1) ||
                 dfs(row, col - 1, index + 1) ||
                 dfs(row, col + 1, index + 1);
    board[row][col] = temp;

    return found;
  }

  for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
      if (dfs(i, j, 0)) return true;
    }
  }
  return false;
}

void main() {
  List<List<String>> board = [
    ['A', 'B', 'C', 'E'],
    ['S', 'F', 'C', 'S'],
    ['A', 'D', 'E', 'E']
  ];
  print(exist(board, "ABCCED")); // Output: true
}
```

### C#

```csharp
public class Solution {
    public bool Exist(char[][] board, string word) {
        int rows = board.Length;
        int cols = board[0].Length;

        bool Dfs(int row, int col, int index) {
            if (index == word.Length) return true;
            if (row < 0 || row >= rows || col < 0 || col >= cols || board[row][col] != word[index]) return false;

            char temp = board[row][col];
            board[row][col] = '#';
            bool found = Dfs(row - 1, col, index + 1) ||
                         Dfs(row + 1, col, index + 1) ||
                         Dfs(row, col - 1, index + 1) ||
                         Dfs(row, col + 1, index + 1);
            board[row][col] = temp;

            return found;
        }

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (Dfs(i, j, 0)) return true;
            }
        }

        return false;
    }
}
```

### Java

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        int rows = board.length;
        int cols = board[0].length;

        boolean dfs(int row, int col, int index) {
            if (index == word.length()) return true;
            if (row < 0 || row >= rows || col < 0 || col >= cols || board[row][col] != word.charAt(index)) return false;

            char temp = board[row][col];
            board[row][col] = '#';
            boolean found = dfs(row - 1, col, index + 1) ||
                            dfs(row + 1, col, index + 1) ||
                            dfs(row, col - 1, index + 1) ||
                            dfs(row, col + 1, index + 1);
            board[row][col] = temp;

            return found;
        }

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (dfs(i, j, 0)) return true;
            }
        }

        return false;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun exist(board: Array<CharArray>, word: String): Boolean {
        for (i in board.indices) {
            for (j in board[0].indices) {
                if (dfs(board, word, i, j, 0)) return true
            }
        }
        return false
    }

    private fun dfs(board: Array<CharArray>, word: String, i: Int, j: Int, index: Int): Boolean {
        if (index == word.length) return true
        if (i !in board.indices || j !in board[0].indices || board[i][j] != word[index]) return false

        val temp = board[i][j]
        board[i][j] = '#'
        val found = dfs(board, word, i - 1, j, index + 1) ||
                    dfs(board, word, i + 1, j, index + 1) ||
                    dfs(board, word, i, j - 1, index + 1) ||
                    dfs(board, word, i, j + 1, index + 1)
        board[i][j] = temp
        return found
    }
}

fun main() {
    val board = arrayOf(
        charArrayOf('A', 'B', 'C', 'E'),
        charArrayOf('S', 'F', 'C', 'S'),
        charArrayOf('A', 'D', 'E', 'E')
    )
    println(Solution().exist(board, "ABCCED")) // Output: true
}
```

### Swift

```swift
class Solution {
    func exist(_ board: [[Character]], _ word: String) -> Bool {
        let rows = board.count
        let cols = board[0].count

        func dfs(_ row: Int, _ col: Int, _ index: Int) -> Bool {
            if index == word.count { return true }
            if row < 0 || row >= rows || col < 0 || col >= cols || board[row][col] != Array(word)[index] {
                return false
            }

            var board = board
            let temp = board[row][col]
            board[row][col] = "#"

            let found = dfs(row - 1, col, index + 1) ||
                        dfs(row + 1, col, index + 1) ||
                        dfs(row, col - 1, index + 1) ||
                        dfs(row, col + 1, index + 1)

            board[row][col] = temp
            return found
        }

        for i in 0..<rows {
            for j in 0..<cols {
                if dfs(i, j, 0) { return true }
            }
        }

        return false
    }
}

let board: [[Character]] = [
    ["A", "B", "C", "E"],
    ["S", "F", "C", "S"],
    ["A", "D", "E", "E"]
]
print(Solution().exist(board, "ABCCED")) // Output: true
```

### The End

