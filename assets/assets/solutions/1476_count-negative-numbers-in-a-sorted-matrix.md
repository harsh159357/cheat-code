# Count Negative Numbers in a Sorted Matrix

## Problem Statement

Given a `m x n` matrix `grid` sorted in non-increasing order both row-wise and column-wise, return the number of negative numbers in the grid.

## Input

```text
grid = [
    [4, 3, 2, -1],
    [3, 2, 1, -1],
    [1, 1, -1, -2],
    [-1, -1, -2, -3]
]
```

## Output

```text
8
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun countNegatives(grid: Array<IntArray>): Int {
        var count = 0
        val rows = grid.size
        val cols = grid[0].size
        var row = 0
        var col = cols - 1

        while (row < rows && col >= 0) {
            if (grid[row][col] < 0) {
                count += rows - row
                col--
            } else {
                row++
            }
        }

        return count
    }
}
```

### Dart

```dart
int countNegatives(List<List<int>> grid) {
  int count = 0;
  int rows = grid.length;
  int cols = grid[0].length;
  int row = 0, col = cols - 1;

  while (row < rows && col >= 0) {
    if (grid[row][col] < 0) {
      count += rows - row;
      col--;
    } else {
      row++;
    }
  }

  return count;
}
```

### C#

```csharp
public class Solution {
    public int CountNegatives(int[][] grid) {
        int count = 0;
        int rows = grid.Length;
        int cols = grid[0].Length;
        int row = 0, col = cols - 1;

        while (row < rows && col >= 0) {
            if (grid[row][col] < 0) {
                count += rows - row;
                col--;
            } else {
                row++;
            }
        }

        return count;
    }
}
```

### Java

```java
class Solution {
    public int countNegatives(int[][] grid) {
        int count = 0;
        int rows = grid.length;
        int cols = grid[0].length;
        int row = 0, col = cols - 1;

        while (row < rows && col >= 0) {
            if (grid[row][col] < 0) {
                count += rows - row;
                col--;
            } else {
                row++;
            }
        }

        return count;
    }
}
```

### Swift

```swift
class Solution {
    func countNegatives(_ grid: [[Int]]) -> Int {
        var count = 0
        let rows = grid.count
        let cols = grid[0].count
        var row = 0, col = cols - 1

        while row < rows && col >= 0 {
            if grid[row][col] < 0 {
                count += rows - row
                col -= 1
            } else {
                row += 1
            }
        }

        return count
    }
}
```

### The End