# Search a 2D Matrix II

## Problem Statement

Write an efficient algorithm to search for a value in an `m x n` matrix. This matrix has the following properties:

- Integers in each row are sorted in ascending order from left to right.
- Integers in each column are sorted in ascending order from top to bottom.

## Input

```text
matrix = [
  [1, 4, 7, 11, 15],
  [2, 5, 8, 12, 19],
  [3, 6, 9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
target = 5
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool searchMatrix(List<List<int>> matrix, int target) {
  if (matrix.isEmpty || matrix[0].isEmpty) return false;

  int rows = matrix.length;
  int cols = matrix[0].length;

  int row = 0;
  int col = cols - 1;

  while (row < rows && col >= 0) {
    if (matrix[row][col] == target) {
      return true;
    } else if (matrix[row][col] < target) {
      row++;
    } else {
      col--;
    }
  }

  return false;
}
```

### C#

```csharp
public class Solution {
    public bool SearchMatrix(int[][] matrix, int target) {
        if (matrix.Length == 0 || matrix[0].Length == 0) return false;

        int rows = matrix.Length;
        int cols = matrix[0].Length;

        int row = 0;
        int col = cols - 1;

        while (row < rows && col >= 0) {
            if (matrix[row][col] == target) {
                return true;
            } else if (matrix[row][col] < target) {
                row++;
            } else {
                col--;
            }
        }

        return false;
    }
}
```

### Java

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix.length == 0 || matrix[0].length == 0) return false;

        int rows = matrix.length;
        int cols = matrix[0].length;

        int row = 0;
        int col = cols - 1;

        while (row < rows && col >= 0) {
            if (matrix[row][col] == target) {
                return true;
            } else if (matrix[row][col] < target) {
                row++;
            } else {
                col--;
            }
        }

        return false;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun searchMatrix(matrix: Array<IntArray>, target: Int): Boolean {
        if (matrix.isEmpty() || matrix[0].isEmpty()) return false

        val rows = matrix.size
        val cols = matrix[0].size

        var row = 0
        var col = cols - 1

        while (row < rows && col >= 0) {
            when {
                matrix[row][col] == target -> return true
                matrix[row][col] < target -> row++
                else -> col--
            }
        }

        return false
    }
}
```

### Swift

```swift
class Solution {
    func searchMatrix(_ matrix: [[Int]], _ target: Int) -> Bool {
        if matrix.isEmpty || matrix[0].isEmpty { return false }

        let rows = matrix.count
        let cols = matrix[0].count

        var row = 0
        var col = cols - 1

        while row < rows && col >= 0 {
            if matrix[row][col] == target {
                return true
            } else if matrix[row][col] < target {
                row += 1
            } else {
                col -= 1
            }
        }

        return false
    }
}
```

### The End

