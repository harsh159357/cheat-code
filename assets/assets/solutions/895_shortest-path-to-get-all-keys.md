# Shortest Path to Get All Keys

## Problem Statement

You are given an `m x n` grid, where:

- `@` is your starting point.
- Lowercase letters represent keys that you need to collect.
- Uppercase letters represent locks that you cannot pass through unless you have the corresponding key.
- `.` represents an empty cell.
- `#` represents a wall that you cannot pass through.

Return the minimum number of steps to collect all keys. If it is impossible, return `-1`.

## Input

```text
grid = ["@.a.#", "###.#", "b.A.B"]
```

## Output

```text
8
```

## Solutions

### Kotlin

```kotlin
class Solution {
    private val directions = arrayOf(0 to -1, 0 to 1, 1 to 0, -1 to 0)

    private class State(val x: Int, val y: Int, val steps: Int, var keys: Int)

    fun shortestPathAllKeys(grid: Array<String>): Int {
        val queue = LinkedList<State>()
        val n = grid.size
        val m = grid[0].length

        var start = 0 to 0
        val keys = mutableSetOf<Char>()
        val locks = mutableSetOf<Char>()
        var allKeys = 0

        for (i in 0 until n) {
            for (j in 0 until m) {
                when (grid[i][j]) {
                    '@' -> start = i to j
                    in 'a'..'f' -> {
                        keys.add(grid[i][j])
                        allKeys += 1 shl (grid[i][j] - 'a')
                    }
                    in 'A'..'F' -> locks.add(grid[i][j])
                }
            }
        }

        queue.add(State(start.first, start.second, 0, 0))
        val visited = Array(n) { Array(m) { IntArray(allKeys + 1) { -1 } } }

        while (queue.isNotEmpty()) {
            val node = queue.poll()
            visited[node.x][node.y][node.keys] = node.steps

            for ((dx, dy) in directions) {
                val nx = node.x + dx
                val ny = node.y + dy
                if (nx in 0 until n && ny in 0 until m && grid[nx][ny] != '#') {
                    val nextState = State(nx, ny, node.steps + 1, node.keys)
                    val cell = grid[nx][ny]
                    if (cell in 'a'..'f') {
                        val keyBit = 1 shl (cell - 'a')
                        nextState.keys = nextState.keys or keyBit
                    } else if (cell in 'A'..'F') {
                        val lockBit = 1 shl (cell - 'A')
                        if (nextState.keys and lockBit == 0) continue
                    }
                    if (nextState.keys == allKeys) return nextState.steps
                    if (visited[nx][ny][nextState.keys] == -1) {
                        visited[nx][ny][nextState.keys] = nextState.steps
                        queue.add(nextState)
                    }
                }
            }
        }
        return -1
    }
}
```

### Dart

```dart
class State {
  int x, y, steps, keys;
  State(this.x, this.y, this.steps, this.keys);
}

int shortestPathAllKeys(List<String> grid) {
  final directions = [
    [0, -1],
    [0, 1],
    [1, 0],
    [-1, 0]
  ];
  final queue = Queue<State>();
  final n = grid.length;
  final m = grid[0].length;

  var startX = 0, startY = 0;
  var allKeys = 0;

  for (var i = 0; i < n; i++) {
    for (var j = 0; j < m; j++) {
      final cell = grid[i][j];
      if (cell == '@') {
        startX = i;
        startY = j;
      } else if (cell.codeUnitAt(0) >= 'a'.codeUnitAt(0) &&
          cell.codeUnitAt(0) <= 'f'.codeUnitAt(0)) {
        allKeys |= (1 << (cell.codeUnitAt(0) - 'a'.codeUnitAt(0)));
      }
    }
  }

  queue.add(State(startX, startY, 0, 0));
  final visited = List.generate(
      n, (_) => List.generate(m, (_) => List.filled(64, false)));

  while (queue.isNotEmpty) {
    final node = queue.removeFirst();
    if (node.keys == allKeys) return node.steps;

    for (final dir in directions) {
      final nx = node.x + dir[0];
      final ny = node.y + dir[1];
      if (nx >= 0 &&
          nx < n &&
          ny >= 0 &&
          ny < m &&
          grid[nx][ny] != '#' &&
          !visited[nx][ny][node.keys]) {
        final cell = grid[nx][ny];
        var nextKeys = node.keys;
        if (cell.codeUnitAt(0) >= 'a'.codeUnitAt(0) &&
            cell.codeUnitAt(0) <= 'f'.codeUnitAt(0)) {
          nextKeys |= (1 << (cell.codeUnitAt(0) - 'a'.codeUnitAt(0)));
        } else if (cell.codeUnitAt(0) >= 'A'.codeUnitAt(0) &&
            cell.codeUnitAt(0) <= 'F'.codeUnitAt(0)) {
          final lockBit = 1 << (cell.codeUnitAt(0) - 'A'.codeUnitAt(0));
          if ((nextKeys & lockBit) == 0) continue;
        }

        queue.add(State(nx, ny, node.steps + 1, nextKeys));
        visited[nx][ny][nextKeys] = true;
      }
    }
  }
  return -1;
}
```

### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    private readonly int[][] directions = new int[][] {
        new int[] {0, -1}, new int[] {0, 1}, new int[] {1, 0}, new int[] {-1, 0}
    };

    private class State {
        public int x, y, steps, keys;
        public State(int x, int y, int steps, int keys) {
            this.x = x;
            this.y = y;
            this.steps = steps;
            this.keys = keys;
        }
    }

    public int ShortestPathAllKeys(string[] grid) {
        int n = grid.Length, m = grid[0].Length, allKeys = 0;
        int startX = 0, startY = 0;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                char cell = grid[i][j];
                if (cell == '@') {
                    startX = i; startY = j;
                } else if (cell >= 'a' && cell <= 'f') {
                    allKeys |= (1 << (cell - 'a'));
                }
            }
        }

        var queue = new Queue<State>();
        queue.Enqueue(new State(startX, startY, 0, 0));
        var visited = new bool[n, m, 64];

        while (queue.Count > 0) {
            var node = queue.Dequeue();
            if (node.keys == allKeys) return node.steps;

            foreach (var dir in directions) {
                int nx = node.x + dir[0], ny = node.y + dir[1];
                if (nx >= 0 && nx < n && ny >= 0 && ny < m && grid[nx][ny] != '#' && !visited[nx, ny, node.keys]) {
                    char cell = grid[nx][ny];
                    int nextKeys = node.keys;
                    if (cell >= 'a' && cell <= 'f') {
                        nextKeys |= (1 << (cell - 'a'));
                    } else if (cell >= 'A' && cell <= 'F') {
                        int lockBit = 1 << (cell - 'A');
                        if ((nextKeys & lockBit) == 0) continue;
                    }

                    queue.Enqueue(new State(nx, ny, node.steps + 1, nextKeys));
                    visited[nx, ny, nextKeys] = true;
                }
            }
        }

        return -1;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    private static final int[][] DIRECTIONS = {{0, -1}, {0, 1}, {1, 0}, {-1, 0}};

    private static class State {
        int x, y, steps, keys;
        State(int x, int y, int steps, int keys) {
            this.x = x;
            this.y = y;
            this.steps = steps;
            this.keys = keys;
        }
    }

    public int shortestPathAllKeys(String[] grid) {
        int n = grid.length, m = grid[0].length(), allKeys = 0;
        int startX = 0, startY = 0;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                char cell = grid[i].charAt(j);
                if (cell == '@') {
                    startX = i; startY = j;
                } else if (cell >= 'a' && cell <= 'f') {
                    allKeys |= (1 << (cell - 'a'));
                }
            }
        }

        Queue<State> queue = new LinkedList<>();
        queue.add(new State(startX, startY, 0, 0));
        boolean[][][] visited = new boolean[n][m][64];

        while (!queue.isEmpty()) {
            State node = queue.poll();
            if (node.keys == allKeys) return node.steps;

            for (int[] dir : DIRECTIONS) {
                int nx = node.x + dir[0], ny = node.y + dir[1];
                if (nx >= 0 && nx < n && ny >= 0 && ny < m && grid[nx].charAt(ny) != '#' && !visited[nx][ny][node.keys]) {
                    char cell = grid[nx].charAt(ny);
                    int nextKeys = node.keys;
                    if (cell >= 'a' && cell <= 'f') {
                        nextKeys |= (1 << (cell - 'a'));
                    } else if (cell >= 'A' && cell <= 'F') {
                        int lockBit = 1 << (cell - 'A');
                        if ((nextKeys & lockBit) == 0) continue;
                    }

                    queue.add(new State(nx, ny, node.steps + 1, nextKeys));
                    visited[nx][ny][nextKeys] = true;
                }
            }
        }

        return -1;
    }
}
```

### Swift

```swift
class Solution {
    private let directions = [(0, -1), (0, 1), (1, 0), (-1, 0)]

    private struct State {
        let x: Int, y: Int, steps: Int, keys: Int
    }

    func shortestPathAllKeys(_ grid: [String]) -> Int {
        let n = grid.count, m = grid[0].count
        var allKeys = 0, startX = 0, startY = 0
        var visited = Array(repeating: Array(repeating: Array(repeating: false, count: 64), count: m), count: n)

        for i in 0..<n {
            for j in 0..<m {
                let cell = Array(grid[i])[j]
                if cell == "@" {
                    startX = i; startY = j
                } else if cell >= "a" && cell <= "f" {
                    allKeys |= (1 << (cell.asciiValue! - Character("a").asciiValue!))
                }
            }
        }

        var queue = [State(x: startX, y: startY, steps: 0, keys: 0)]

        while !queue.isEmpty {
            let node = queue.removeFirst()
            if node.keys == allKeys { return node.steps }

            for dir in directions {
                let nx = node.x + dir.0, ny = node.y + dir.1
                if nx >= 0 && nx < n && ny >= 0 && ny < m && !visited[nx][ny][node.keys] {
                    let cell = Array(grid[nx])[ny]
                    var nextKeys = node.keys
                    if cell >= "a" && cell <= "f" {
                        nextKeys |= (1 << (cell.asciiValue! - Character("a").asciiValue!))
                    } else if cell >= "A" && cell <= "F" {
                        let lockBit = 1 << (cell.asciiValue! - Character("A").asciiValue!)
                        if (nextKeys & lockBit) == 0 { continue }
                    }
                    visited[nx][ny][nextKeys] = true
                    queue.append(State(x: nx, y: ny, steps: node.steps + 1, keys: nextKeys))
                }
            }
        }

        return -1
    }
}
```

### The End