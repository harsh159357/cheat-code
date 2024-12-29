# Nearest Exit from Entrance in Maze

## Problem Statement

You are given an `m x n` matrix `maze` (0-indexed) with walls ('+') and empty spaces ('.'), and you start at the entrance of the maze. You can move up, down, left, or right. Return the number of steps to reach the nearest exit. If there is no way to reach an exit, return `-1`.

An exit is defined as an empty space that is located at the border of the maze, and it is not the entrance.

## Input

```text
maze = [["+", "+", ".", "+"],
        [".", ".", ".", "+"],
        ["+", "+", "+", "."]]
entrance = [1, 2]
```

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun nearestExit(maze: Array<CharArray>, entrance: IntArray): Int {
        val directions = arrayOf(-1, 0, 1, 0, -1)
        val m = maze.size
        val n = maze[0].size
        val queue = LinkedList<IntArray>()
        val visited = Array(m) { BooleanArray(n) }
        queue.offer(entrance)
        visited[entrance[0]][entrance[1]] = true
        var steps = 0

        while (queue.isNotEmpty()) {
            val size = queue.size
            steps++
            for (i in 0 until size) {
                val (x, y) = queue.poll()
                for (d in 0 until 4) {
                    val nx = x + directions[d]
                    val ny = y + directions[d + 1]
                    if (nx < 0 || nx >= m || ny < 0 || ny >= n) {
                        if (!(x == entrance[0] && y == entrance[1])) return steps - 1
                        continue
                    }
                    if (maze[nx][ny] == '.' && !visited[nx][ny]) {
                        visited[nx][ny] = true
                        queue.offer(intArrayOf(nx, ny))
                    }
                }
            }
        }
        return -1
    }
}

fun main() {
    val maze = arrayOf(
        charArrayOf('+', '+', '.', '+'),
        charArrayOf('.', '.', '.', '+'),
        charArrayOf('+', '+', '+', '.')
    )
    val entrance = intArrayOf(1, 2)
    println(Solution().nearestExit(maze, entrance)) // Output: 1
}
```

### Dart

```dart
int nearestExit(List<List<String>> maze, List<int> entrance) {
  List<int> directions = [-1, 0, 1, 0, -1];
  int m = maze.length, n = maze[0].length;
  Queue<List<int>> queue = Queue();
  List<List<bool>> visited = List.generate(m, (_) => List.filled(n, false));

  queue.add(entrance);
  visited[entrance[0]][entrance[1]] = true;
  int steps = 0;

  while (queue.isNotEmpty) {
    int size = queue.length;
    steps++;
    for (int i = 0; i < size; i++) {
      List<int> curr = queue.removeFirst();
      for (int d = 0; d < 4; d++) {
        int nx = curr[0] + directions[d];
        int ny = curr[1] + directions[d + 1];
        if (nx < 0 || nx >= m || ny < 0 || ny >= n) {
          if (!(curr[0] == entrance[0] && curr[1] == entrance[1])) {
            return steps - 1;
          }
          continue;
        }
        if (maze[nx][ny] == '.' && !visited[nx][ny]) {
          visited[nx][ny] = true;
          queue.add([nx, ny]);
        }
      }
    }
  }

  return -1;
}

void main() {
  List<List<String>> maze = [
    ['+', '+', '.', '+'],
    ['.', '.', '.', '+'],
    ['+', '+', '+', '.']
  ];
  List<int> entrance = [1, 2];
  print(nearestExit(maze, entrance)); // Output: 1
}
```

### C#

```csharp
public class Solution {
    public int NearestExit(char[][] maze, int[] entrance) {
        int[] directions = {-1, 0, 1, 0, -1};
        int m = maze.Length, n = maze[0].Length;
        Queue<int[]> queue = new Queue<int[]>();
        bool[,] visited = new bool[m, n];

        queue.Enqueue(entrance);
        visited[entrance[0], entrance[1]] = true;
        int steps = 0;

        while (queue.Count > 0) {
            int size = queue.Count;
            steps++;
            for (int i = 0; i < size; i++) {
                int[] curr = queue.Dequeue();
                for (int d = 0; d < 4; d++) {
                    int nx = curr[0] + directions[d];
                    int ny = curr[1] + directions[d + 1];
                    if (nx < 0 || nx >= m || ny < 0 || ny >= n) {
                        if (!(curr[0] == entrance[0] && curr[1] == entrance[1])) {
                            return steps - 1;
                        }
                        continue;
                    }
                    if (maze[nx][ny] == '.' && !visited[nx, ny]) {
                        visited[nx, ny] = true;
                        queue.Enqueue(new int[] { nx, ny });
                    }
                }
            }
        }

        return -1;
    }
}
```

### The End