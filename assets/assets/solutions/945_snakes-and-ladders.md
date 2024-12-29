# Snakes and Ladders

## Problem Statement

You are given an `n x n` integer matrix `board` where the cells represent a Snakes and Ladders game:

- The player starts at square `1` and takes turns rolling a six-sided die.
- The board contains `-1` for empty cells or positive integers to indicate a jump to a specific square.
- Return the minimum number of moves required to reach the last square (`n * n`). If it is not possible, return `-1`.

## Input

```text
board = [
    [-1,-1,-1,-1,-1,-1],
    [-1,-1,-1,-1,-1,-1],
    [-1,-1,-1,-1,-1,-1],
    [-1,35,-1,-1,13,-1],
    [-1,-1,-1,-1,-1,-1],
    [-1,15,-1,-1,-1,-1]
]
```

## Output

```text
4
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun snakesAndLadders(board: Array<IntArray>): Int {
        val n = board.size
        val visited = BooleanArray(n * n + 1)
        val queue = LinkedList<Int>()
        queue.offer(1)
        var moves = 0

        while (queue.isNotEmpty()) {
            val size = queue.size
            for (i in 0 until size) {
                val curr = queue.poll()
                if (curr == n * n) return moves
                if (visited[curr]) continue
                visited[curr] = true

                for (j in 1..6) {
                    val next = curr + j
                    if (next > n * n) break
                    val (x, y) = getPosition(next, n)
                    val num = if (board[x][y] == -1) next else board[x][y]
                    queue.offer(num)
                }
            }
            moves++
        }
        return -1
    }

    private fun getPosition(num: Int, n: Int): Pair<Int, Int> {
        val row = (num - 1) / n
        val col = if (row % 2 == 0) (num - 1) % n else n - 1 - (num - 1) % n
        val x = n - 1 - row
        val y = col
        return Pair(x, y)
    }
}
```

### Dart

```dart
import 'dart:collection';

int snakesAndLadders(List<List<int>> board) {
  int n = board.length;
  List<bool> visited = List.filled(n * n + 1, false);
  Queue<int> queue = Queue();
  queue.add(1);
  int moves = 0;

  while (queue.isNotEmpty) {
    int size = queue.length;
    for (int i = 0; i < size; i++) {
      int curr = queue.removeFirst();
      if (curr == n * n) return moves;
      if (visited[curr]) continue;
      visited[curr] = true;

      for (int j = 1; j <= 6; j++) {
        int next = curr + j;
        if (next > n * n) break;
        var pos = _getPosition(next, n);
        int num = board[pos[0]][pos[1]] == -1 ? next : board[pos[0]][pos[1]];
        queue.add(num);
      }
    }
    moves++;
  }
  return -1;
}

List<int> _getPosition(int num, int n) {
  int row = (num - 1) ~/ n;
  int col = row % 2 == 0 ? (num - 1) % n : n - 1 - (num - 1) % n;
  int x = n - 1 - row;
  int y = col;
  return [x, y];
}
```

### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public int SnakesAndLadders(int[][] board) {
        int n = board.Length;
        bool[] visited = new bool[n * n + 1];
        Queue<int> queue = new Queue<int>();
        queue.Enqueue(1);
        int moves = 0;

        while (queue.Count > 0) {
            int size = queue.Count;
            for (int i = 0; i < size; i++) {
                int curr = queue.Dequeue();
                if (curr == n * n) return moves;
                if (visited[curr]) continue;
                visited[curr] = true;

                for (int j = 1; j <= 6; j++) {
                    int next = curr + j;
                    if (next > n * n) break;
                    var pos = GetPosition(next, n);
                    int num = board[pos.Item1][pos.Item2] == -1 ? next : board[pos.Item1][pos.Item2];
                    queue.Enqueue(num);
                }
            }
            moves++;
        }
        return -1;
    }

    private (int, int) GetPosition(int num, int n) {
        int row = (num - 1) / n;
        int col = row % 2 == 0 ? (num - 1) % n : n - 1 - (num - 1) % n;
        int x = n - 1 - row;
        int y = col;
        return (x, y);
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int snakesAndLadders(int[][] board) {
        int n = board.length;
        boolean[] visited = new boolean[n * n + 1];
        Queue<Integer> queue = new LinkedList<>();
        queue.offer(1);
        int moves = 0;

        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                int curr = queue.poll();
                if (curr == n * n) return moves;
                if (visited[curr]) continue;
                visited[curr] = true;

                for (int j = 1; j <= 6; j++) {
                    int next = curr + j;
                    if (next > n * n) break;
                    int[] pos = getPosition(next, n);
                    int num = board[pos[0]][pos[1]] == -1 ? next : board[pos[0]][pos[1]];
                    queue.offer(num);
                }
            }
            moves++;
        }
        return -1;
    }

    private int[] getPosition(int num, int n) {
        int row = (num - 1) / n;
        int col = row % 2 == 0 ? (num - 1) % n : n - 1 - (num - 1) % n;
        int x = n - 1 - row;
        int y = col;
        return new int[]{x, y};
    }
}
```

### Swift

```swift
class Solution {
    func snakesAndLadders(_ board: [[Int]]) -> Int {
        let n = board.count
        var visited = Array(repeating: false, count: n * n + 1)
        var queue: [Int] = [1]
        var moves = 0

        while !queue.isEmpty {
            let size = queue.count
            for _ in 0..<size {
                let curr = queue.removeFirst()
                if curr == n * n { return moves }
                if visited[curr] { continue }
                visited[curr] = true

                for j in 1...6 {
                    let next = curr + j
                    if next > n * n { break }
                    let pos = getPosition(next, n)
                    let num = board[pos.0][pos.1] == -1 ? next : board[pos.0][pos.1]
                    queue.append(num)
                }
            }
            moves += 1
        }
        return -1
    }

    private func getPosition(_ num: Int, _ n: Int) -> (Int, Int) {
        let row = (num - 1) / n
        let col = row % 2 == 0 ? (num - 1) % n : n - 1 - (num - 1) % n
        let x = n - 1 - row
        let y = col
        return (x, y)
    }
}
```

### The End