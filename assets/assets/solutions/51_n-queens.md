# N-Queens

## Problem Statement

The `n`-queens puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return all distinct solutions to the `n`-queens puzzle. Each solution contains a distinct board configuration of the `n`-queens' placement, where `'Q'` and `'.'` indicate a queen and an empty space, respectively.

## Input

```text
n = 4
```

## Output

```text
[
[".Q..",
"...Q",
"Q...",
"..Q."],

["..Q.",
"Q...",
"...Q",
".Q.."]
]

(Explanation: These are the two valid ways to place 4 queens on a 4x4 chessboard.)
```

## Solutions

### Dart

```dart
List<List<String>> solveNQueens(int n) {
  List<List<String>> result = [];
  List<List<String>> board = List.generate(n, (_) => List.filled(n, '.'));
  List<bool> cols = List.filled(n, false);
  List<bool> diagonal1 = List.filled(2 * n - 1, false);
  List<bool> diagonal2 = List.filled(2 * n - 1, false);

  void backtrack(int row) {
    if (row == n) {
      result.add(board.map((row) => row.join()).toList());
      return;
    }
    for (int col = 0; col < n; col++) {
      if (!cols[col] && !diagonal1[row + col] && !diagonal2[row - col + n - 1]) {
        board[row][col] = 'Q';
        cols[col] = true;
        diagonal1[row + col] = true;
        diagonal2[row - col + n - 1] = true;
        backtrack(row + 1);
        board[row][col] = '.';
        cols[col] = false;
        diagonal1[row + col] = false;
        diagonal2[row - col + n - 1] = false;
      }
    }
  }

  backtrack(0);
  return result;
}

void main() {
  print(solveNQueens(4));
}
```

### C#

```csharp
public class Solution {
    public IList<IList<string>> SolveNQueens(int n) {
        IList<IList<string>> result = new List<IList<string>>();
        char[][] board = new char[n][];
        for (int i = 0; i < n; i++) board[i] = new string('.', n).ToCharArray();
        bool[] cols = new bool[n];
        bool[] diagonal1 = new bool[2 * n - 1];
        bool[] diagonal2 = new bool[2 * n - 1];

        void Backtrack(int row) {
            if (row == n) {
                result.Add(board.Select(r => new string(r)).ToList());
                return;
            }
            for (int col = 0; col < n; col++) {
                if (!cols[col] && !diagonal1[row + col] && !diagonal2[row - col + n - 1]) {
                    board[row][col] = 'Q';
                    cols[col] = true;
                    diagonal1[row + col] = true;
                    diagonal2[row - col + n - 1] = true;
                    Backtrack(row + 1);
                    board[row][col] = '.';
                    cols[col] = false;
                    diagonal1[row + col] = false;
                    diagonal2[row - col + n - 1] = false;
                }
            }
        }

        Backtrack(0);
        return result;
    }
}
```

### Java

```java
class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> result = new ArrayList<>();
        char[][] board = new char[n][n];
        for (char[] row : board) Arrays.fill(row, '.');
        boolean[] cols = new boolean[n];
        boolean[] diagonal1 = new boolean[2 * n - 1];
        boolean[] diagonal2 = new boolean[2 * n - 1];

        backtrack(0);

        void backtrack(int row) {
            if (row == n) {
                result.add(
                    Arrays.stream(board).map(String::new).collect(Collectors.toList())
                );
                return;
            }
            for (int col = 0; col < n; col++) {
                if (!cols[col] && !diagonal1[row + col] && !diagonal2[row - col + n - 1]) {
                    board[row][col] = 'Q';
                    cols[col] = true;
                    diagonal1[row + col] = true;
                    diagonal2[row - col + n - 1] = true;
                    backtrack(row + 1);
                    board[row][col] = '.';
                    cols[col] = false;
                    diagonal1[row + col] = false;
                    diagonal2[row - col + n - 1] = false;
                }
            }
        }

        backtrack(0);
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun solveNQueens(n: Int): List<List<String>> {
        val result = mutableListOf<List<String>>()
        val board = Array(n) { CharArray(n) { '.' } }
        val cols = BooleanArray(n)
        val diagonal1 = BooleanArray(2 * n - 1)
        val diagonal2 = BooleanArray(2 * n - 1)

        fun isSafe(row: Int, col: Int): Boolean {
            return !cols[col] && !diagonal1[row + col] && !diagonal2[row - col + n - 1]
        }

        fun placeQueen(row: Int, col: Int) {
            board[row][col] = 'Q'
            cols[col] = true
            diagonal1[row + col] = true
            diagonal2[row - col + n - 1] = true
        }

        fun removeQueen(row: Int, col: Int) {
            board[row][col] = '.'
            cols[col] = false
            diagonal1[row + col] = false
            diagonal2[row - col + n - 1] = false
        }

        fun backtrack(row: Int) {
            if (row == n) {
                result.add(board.map { it.joinToString("") })
                return
            }
            for (col in 0 until n) {
                if (isSafe(row, col)) {
                    placeQueen(row, col)
                    backtrack(row + 1)
                    removeQueen(row, col)
                }
            }
        }

        backtrack(0)
        return result
    }
}
```

### Swift

```swift
class Solution {
    func solveNQueens(_ n: Int) -> [[String]] {
        var result = [[String]]()
        var board = Array(repeating: Array(repeating: ".", count: n), count: n)
        var cols = Array(repeating: false, count: n)
        var diagonal1 = Array(repeating: false, count: 2 * n - 1)
        var diagonal2 = Array(repeating: false, count: 2 * n - 1)

        func backtrack(row: Int) {
            if row == n {
                result.append(board.map { $0.joined() })
                return
            }
            for col in 0..<n {
                if !cols[col] && !diagonal1[row + col] && !diagonal2[row - col + n - 1] {
                    board[row][col] = "Q"
                    cols[col] = true
                    diagonal1[row + col] = true
                    diagonal2[row - col + n - 1] = true
                    backtrack(row: row + 1)
                    board[row][col] = "."
                    cols[col] = false
                    diagonal1[row + col] = false
                    diagonal2[row - col + n - 1] = false
                }
            }
        }

        backtrack(row: 0)
        return result
    }
}

let solution = Solution()
print(solution.solveNQueens(4))
```

### The End

