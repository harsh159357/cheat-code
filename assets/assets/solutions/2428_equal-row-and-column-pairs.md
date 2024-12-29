# Equal Row and Column Pairs

## Problem Statement

You are given a 2D integer array `grid` of size `n x n`.  
Find the number of pairs `(r, c)` such that the `r-th` row and `c-th` column are equal.

## Input

```text
grid = [[3, 2, 1],
        [2, 7, 7],
        [1, 7, 7]]
```

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun equalPairs(grid: Array<IntArray>): Int {
        var count = 0

        for (i in grid.indices) {
            val column = IntArray(grid.size) { j -> grid[j][i] }

            for (row in grid) {
                if (column contentEquals row) {
                    count++
                }
            }
        }

        return count
    }
}

fun main() {
    val grid = arrayOf(
        intArrayOf(3, 2, 1),
        intArrayOf(2, 7, 7),
        intArrayOf(1, 7, 7)
    )
    println(Solution().equalPairs(grid)) // Output: 1
}
```

### Dart

```dart
int equalPairs(List<List<int>> grid) {
  int count = 0;

  for (int i = 0; i < grid.length; i++) {
    List<int> column = [for (int j = 0; j < grid.length; j++) grid[j][i]];

    for (List<int> row in grid) {
      if (ListEquality().equals(row, column)) {
        count++;
      }
    }
  }

  return count;
}

void main() {
  List<List<int>> grid = [
    [3, 2, 1],
    [2, 7, 7],
    [1, 7, 7]
  ];
  print(equalPairs(grid)); // Output: 1
}
```

### C#

```csharp
public class Solution {
    public int EqualPairs(int[][] grid) {
        int count = 0;

        for (int i = 0; i < grid.Length; i++) {
            int[] column = new int[grid.Length];
            for (int j = 0; j < grid.Length; j++) {
                column[j] = grid[j][i];
            }

            foreach (int[] row in grid) {
                if (row.SequenceEqual(column)) {
                    count++;
                }
            }
        }

        return count;
    }
}
```

### Java

```java
class Solution {
    public int equalPairs(int[][] grid) {
        int count = 0;

        for (int i = 0; i < grid.length; i++) {
            int[] column = new int[grid.length];
            for (int j = 0; j < grid.length; j++) {
                column[j] = grid[j][i];
            }

            for (int[] row : grid) {
                if (Arrays.equals(row, column)) {
                    count++;
                }
            }
        }

        return count;
    }
}
```

### Swift

```swift
class Solution {
    func equalPairs(_ grid: [[Int]]) -> Int {
        var count = 0

        for i in 0..<grid.count {
            let column = grid.map { $0[i] }

            for row in grid {
                if row == column {
                    count += 1
                }
            }
        }

        return count
    }
}

let grid = [
    [3, 2, 1],
    [2, 7, 7],
    [1, 7, 7]
]
print(Solution().equalPairs(grid)) // Output: 1
```

### The End