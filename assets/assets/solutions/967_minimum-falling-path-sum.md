# Minimum Falling Path Sum

## Problem Statement

Given an `n x n` integer matrix, return the minimum sum of any falling path through the matrix.

A falling path starts at any element in the first row and chooses one element from each row. The next row's choice must be from the column directly below or a column immediately adjacent.

## Input

```text
matrix = [[2,1,3],[6,5,4],[7,8,9]]
```

## Output

```text
13
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun minFallingPathSum(matrix: Array<IntArray>): Int {
        val n = matrix.size
        if (n == 1) return matrix[0][0]

        val paths = Array(2) { IntArray(n) }
        paths[0] = matrix[0]
        for (i in 1 until n) {
            for (j in 0 until n) {
                val leftAncestor = paths[0][maxOf(j - 1, 0)]
                val topAncestor = paths[0][j]
                val rightAncestor = paths[0][minOf(j + 1, n - 1)]
                val bestAncestor = minOf(topAncestor, leftAncestor, rightAncestor)
                paths[1][j] = matrix[i][j] + bestAncestor
            }
            paths[0] = paths[1].copyOf()
        }
        return paths[1].minOrNull() ?: 0
    }
}
```

### Dart

```dart
int minFallingPathSum(List<List<int>> matrix) {
  int n = matrix.length;
  if (n == 1) return matrix[0][0];

  List<int> prevRow = List.from(matrix[0]);
  List<int> curRow = List.filled(n, 0);

  for (int i = 1; i < n; i++) {
    for (int j = 0; j < n; j++) {
      int leftAncestor = prevRow[(j - 1).clamp(0, n - 1)];
      int topAncestor = prevRow[j];
      int rightAncestor = prevRow[(j + 1).clamp(0, n - 1)];
      curRow[j] = matrix[i][j] + [topAncestor, leftAncestor, rightAncestor].reduce((a, b) => a < b ? a : b);
    }
    prevRow = List.from(curRow);
  }

  return curRow.reduce((a, b) => a < b ? a : b);
}
```

### C#

```csharp
public class Solution {
    public int MinFallingPathSum(int[][] matrix) {
        int n = matrix.Length;
        if (n == 1) return matrix[0][0];

        int[] prevRow = (int[])matrix[0].Clone();
        int[] curRow = new int[n];

        for (int i = 1; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int leftAncestor = prevRow[Math.Max(j - 1, 0)];
                int topAncestor = prevRow[j];
                int rightAncestor = prevRow[Math.Min(j + 1, n - 1)];
                curRow[j] = matrix[i][j] + Math.Min(topAncestor, Math.Min(leftAncestor, rightAncestor));
            }
            Array.Copy(curRow, prevRow, n);
        }

        return curRow.Min();
    }
}
```

### Java

```java
class Solution {
    public int minFallingPathSum(int[][] matrix) {
        int n = matrix.length;
        if (n == 1) return matrix[0][0];

        int[] prevRow = matrix[0].clone();
        int[] curRow = new int[n];

        for (int i = 1; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int leftAncestor = prevRow[Math.max(j - 1, 0)];
                int topAncestor = prevRow[j];
                int rightAncestor = prevRow[Math.min(j + 1, n - 1)];
                curRow[j] = matrix[i][j] + Math.min(topAncestor, Math.min(leftAncestor, rightAncestor));
            }
            System.arraycopy(curRow, 0, prevRow, 0, n);
        }

        int result = Integer.MAX_VALUE;
        for (int num : curRow) {
            result = Math.min(result, num);
        }
        return result;
    }
}
```

### Swift

```swift
class Solution {
    func minFallingPathSum(_ matrix: [[Int]]) -> Int {
        let n = matrix.count
        if n == 1 { return matrix[0][0] }

        var prevRow = matrix[0]
        var curRow = Array(repeating: 0, count: n)

        for i in 1..<n {
            for j in 0..<n {
                let leftAncestor = prevRow[max(j - 1, 0)]
                let topAncestor = prevRow[j]
                let rightAncestor = prevRow[min(j + 1, n - 1)]
                curRow[j] = matrix[i][j] + min(topAncestor, min(leftAncestor, rightAncestor))
            }
            prevRow = curRow
        }

        return curRow.min() ?? 0
    }
}
```

### The End