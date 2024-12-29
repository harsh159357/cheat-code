# Valid Sudoku

## Problem Statement

Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

The Sudoku board could be partially filled, where empty cells are filled with the character `'.'`.

## Input

```text
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
```

## Output

```text
`true`  
(Explanation: The board is valid according to Sudoku rules.)
```

## Solutions

### Dart

```dart
bool isValidSudoku(List<List<String>> board) {
  List<List<bool>> rows = List.generate(9, (_) => List.filled(9, false));
  List<List<bool>> cols = List.generate(9, (_) => List.filled(9, false));
  List<List<List<bool>>> boxes = List.generate(3, (_) => List.generate(3, (_) => List.filled(9, false)));

  for (int i = 0; i < 9; i++) {
    for (int j = 0; j < 9; j++) {
      if (board[i][j] != '.') {
        int num = int.parse(board[i][j]) - 1;
        if (rows[i][num] || cols[j][num] || boxes[i ~/ 3][j ~/ 3][num]) {
          return false;
        }
        rows[i][num] = true;
        cols[j][num] = true;
        boxes[i ~/ 3][j ~/ 3][num] = true;
      }
    }
  }
  return true;
}

void main() {
  List<List<String>> board1 = [
    ['5', '3', '.', '.', '7', '.', '.', '.', '.'],
    ['6', '.', '.', '1', '9', '5', '.', '.', '.'],
    ['.', '9', '8', '.', '.', '.', '.', '6', '.'],
    ['8', '.', '.', '.', '6', '.', '.', '.', '3'],
    ['4', '.', '.', '8', '.', '3', '.', '.', '1'],
    ['7', '.', '.', '.', '2', '.', '.', '.', '6'],
    ['.', '6', '.', '.', '.', '.', '2', '8', '.'],
    ['.', '.', '.', '4', '1', '9', '.', '.', '5'],
    ['.', '.', '.', '.', '8', '.', '.', '7', '9']
  ];
  print(isValidSudoku(board1)); // Output: true
}
```

### C#

```csharp
public class Solution {
    public bool IsValidSudoku(char[][] board) {
        bool[,] rows = new bool[9,9];
        bool[,] cols = new bool[9,9];
        bool[,,] boxes = new bool[3,3,9];

        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                if (board[i][j] != '.') {
                    int num = board[i][j] - '1';
                    if (rows[i, num] || cols[j, num] || boxes[i / 3, j / 3, num]) {
                        return false;
                    }
                    rows[i, num] = true;
                    cols[j, num] = true;
                    boxes[i / 3, j / 3, num] = true;
                }
            }
        }
        return true;
    }
}
```

### Java

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        boolean[][] rows = new boolean[9][9];
        boolean[][] cols = new boolean[9][9];
        boolean[][][] boxes = new boolean[3][3][9];

        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                if (board[i][j] != '.') {
                    int num = board[i][j] - '1';
                    if (rows[i][num] || cols[j][num] || boxes[i / 3][j / 3][num]) {
                        return false;
                    }
                    rows[i][num] = true;
                    cols[j][num] = true;
                    boxes[i / 3][j / 3][num] = true;
                }
            }
        }
        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isValidSudoku(board: Array<CharArray>): Boolean {
        val rows = Array(9) { BooleanArray(9) }
        val cols = Array(9) { BooleanArray(9) }
        val boxes = Array(3) { Array(3) { BooleanArray(9) } }

        for (i in 0 until 9) {
            for (j in 0 until 9) {
                val char = board[i][j]
                if (char != '.') {
                    val num = char - '1'
                    if (rows[i][num] || cols[j][num] || boxes[i / 3][j / 3][num]) {
                        return false
                    }
                    rows[i][num] = true
                    cols[j][num] = true
                    boxes[i / 3][j / 3][num] = true
                }
            }
        }
        return true
    }
}
```

### Swift

```swift
class Solution {
    func isValidSudoku(_ board: [[Character]]) -> Bool {
        var rows = Array(repeating: Array(repeating: false, count: 9), count: 9)
        var cols = Array(repeating: Array(repeating: false, count: 9), count: 9)
        var boxes = Array(repeating: Array(repeating: Array(repeating: false, count: 9), count: 3), count: 3)

        for i in 0..<9 {
            for j in 0..<9 {
                if board[i][j] != "." {
                    let num = Int(board[i][j].asciiValue! - Character("1").asciiValue!)
                    if rows[i][num] || cols[j][num] || boxes[i / 3][j / 3][num] {
                        return false
                    }
                    rows[i][num] = true
                    cols[j][num] = true
                    boxes[i / 3][j / 3][num] = true
                }
            }
        }
        return true
    }
}

let solution = Solution()
let board1: [[Character]] = [
    ["5", "3", ".", ".", "7", ".", ".", ".", "."],
    ["6", ".", ".", "1", "9", "5", ".", ".", "."],
    [".", "9", "8", ".", ".", ".", ".", "6", "."],
    ["8", ".", ".", ".", "6", ".", ".", ".", "3"],
    ["4", ".", ".", "8", ".", "3", ".", ".", "1"],
    ["7", ".", ".", ".", "2", ".", ".", ".", "6"],
    [".", "6", ".", ".", ".", ".", "2", "8", "."],
    [".", ".", ".", "4", "1", "9", ".", ".", "5"],
    [".", ".", ".", ".", "8", ".", ".", "7", "9"]
]
print(solution.isValidSudoku(board1)) // Output: true
```


### The End

