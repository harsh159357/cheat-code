# Find Winner on a Tic Tac Toe Game

## Problem Statement

Given a `3x3` Tic Tac Toe board represented by the sequence of moves by two players (`A` and `B`), determine the winner or the game's status.

- Return `"A"` if player `A` wins.
- Return `"B"` if player `B` wins.
- Return `"Draw"` if all cells are filled, and there is no winner.
- Return `"Pending"` if the game is still ongoing.

## Input

```text
moves = [[0,0],[2,0],[1,1],[2,1],[2,2]]
```

## Output

```text
"A"
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun tictactoe(moves: Array<IntArray>): String {
        val rows = IntArray(3)
        val cols = IntArray(3)
        var diagonal = 0
        var antiDiagonal = 0

        for ((index, move) in moves.withIndex()) {
            val player = if (index % 2 == 0) 1 else -1
            val row = move[0]
            val col = move[1]

            rows[row] += player
            cols[col] += player

            if (row == col) {
                diagonal += player
            }

            if (row + col == 2) {
                antiDiagonal += player
            }

            if (rows[row] == 3 || cols[col] == 3 || diagonal == 3 || antiDiagonal == 3) {
                return "A"
            } else if (rows[row] == -3 || cols[col] == -3 || diagonal == -3 || antiDiagonal == -3) {
                return "B"
            }
        }

        return if (moves.size == 9) "Draw" else "Pending"
    }
}
```

### Dart

```dart
String tictactoe(List<List<int>> moves) {
  List<int> rows = List.filled(3, 0);
  List<int> cols = List.filled(3, 0);
  int diagonal = 0;
  int antiDiagonal = 0;

  for (int i = 0; i < moves.length; i++) {
    int player = i % 2 == 0 ? 1 : -1;
    int row = moves[i][0];
    int col = moves[i][1];

    rows[row] += player;
    cols[col] += player;

    if (row == col) diagonal += player;
    if (row + col == 2) antiDiagonal += player;

    if (rows[row] == 3 || cols[col] == 3 || diagonal == 3 || antiDiagonal == 3) {
      return "A";
    } else if (rows[row] == -3 || cols[col] == -3 || diagonal == -3 || antiDiagonal == -3) {
      return "B";
    }
  }

  return moves.length == 9 ? "Draw" : "Pending";
}
```

### C#

```csharp
public class Solution {
    public string Tictactoe(int[][] moves) {
        int[] rows = new int[3];
        int[] cols = new int[3];
        int diagonal = 0;
        int antiDiagonal = 0;

        for (int i = 0; i < moves.Length; i++) {
            int player = i % 2 == 0 ? 1 : -1;
            int row = moves[i][0];
            int col = moves[i][1];

            rows[row] += player;
            cols[col] += player;

            if (row == col) diagonal += player;
            if (row + col == 2) antiDiagonal += player;

            if (rows[row] == 3 || cols[col] == 3 || diagonal == 3 || antiDiagonal == 3) {
                return "A";
            } else if (rows[row] == -3 || cols[col] == -3 || diagonal == -3 || antiDiagonal == -3) {
                return "B";
            }
        }

        return moves.Length == 9 ? "Draw" : "Pending";
    }
}
```

### Java

```java
class Solution {
    public String tictactoe(int[][] moves) {
        int[] rows = new int[3];
        int[] cols = new int[3];
        int diagonal = 0;
        int antiDiagonal = 0;

        for (int i = 0; i < moves.length; i++) {
            int player = i % 2 == 0 ? 1 : -1;
            int row = moves[i][0];
            int col = moves[i][1];

            rows[row] += player;
            cols[col] += player;

            if (row == col) diagonal += player;
            if (row + col == 2) antiDiagonal += player;

            if (rows[row] == 3 || cols[col] == 3 || diagonal == 3 || antiDiagonal == 3) {
                return "A";
            } else if (rows[row] == -3 || cols[col] == -3 || diagonal == -3 || antiDiagonal == -3) {
                return "B";
            }
        }

        return moves.length == 9 ? "Draw" : "Pending";
    }
}
```

### Swift

```swift
class Solution {
    func tictactoe(_ moves: [[Int]]) -> String {
        var rows = [Int](repeating: 0, count: 3)
        var cols = [Int](repeating: 0, count: 3)
        var diagonal = 0
        var antiDiagonal = 0

        for (index, move) in moves.enumerated() {
            let player = index % 2 == 0 ? 1 : -1
            let row = move[0]
            let col = move[1]

            rows[row] += player
            cols[col] += player

            if row == col { diagonal += player }
            if row + col == 2 { antiDiagonal += player }

            if rows[row] == 3 || cols[col] == 3 || diagonal == 3 || antiDiagonal == 3 {
                return "A"
            } else if rows[row] == -3 || cols[col] == -3 || diagonal == -3 || antiDiagonal == -3 {
                return "B"
            }
        }

        return moves.count == 9 ? "Draw" : "Pending"
    }
}
```

### The End