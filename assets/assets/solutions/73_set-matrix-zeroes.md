# Set Matrix Zeroes

## Problem Statement

Given an `m x n` integer matrix `matrix`, if an element is 0, set its entire row and column to 0. Do it in place.

## Input

```text
matrix = [
  [1, 1, 1],
  [1, 0, 1],
  [1, 1, 1]
]
```

## Output

```text
[
  [1, 0, 1],
  [0, 0, 0],
  [1, 0, 1]
]
```

## Solutions

### Dart

```dart
void setZeroes(List<List<int>> matrix) {
  final int m = matrix.length;
  final int n = matrix[0].length;
  bool firstRowHasZero = false;
  bool firstColHasZero = false;

  for (int j = 0; j < n; j++) {
    if (matrix[0][j] == 0) {
      firstRowHasZero = true;
      break;
    }
  }

  for (int i = 0; i < m; i++) {
    if (matrix[i][0] == 0) {
      firstColHasZero = true;
      break;
    }
  }

  for (int i = 1; i < m; i++) {
    for (int j = 1; j < n; j++) {
      if (matrix[i][j] == 0) {
        matrix[i][0] = 0;
        matrix[0][j] = 0;
      }
    }
  }

  for (int i = 1; i < m; i++) {
    for (int j = 1; j < n; j++) {
      if (matrix[i][0] == 0 || matrix[0][j] == 0) {
        matrix[i][j] = 0;
      }
    }
  }

  if (firstRowHasZero) {
    for (int j = 0; j < n; j++) {
      matrix[0][j] = 0;
    }
  }

  if (firstColHasZero) {
    for (int i = 0; i < m; i++) {
      matrix[i][0] = 0;
    }
  }
}

void main() {
  var matrix1 = [
    [1, 1, 1],
    [1, 0, 1],
    [1, 1, 1]
  ];
  setZeroes(matrix1);
  print(matrix1); // Output: [[1, 0, 1], [0, 0, 0], [1, 0, 1]]

  var matrix2 = [
    [0, 1, 2, 0],
    [3, 4, 5, 2],
    [1, 3, 1, 5]
  ];
  setZeroes(matrix2);
  print(matrix2); // Output: [[0, 0, 0, 0], [0, 4, 5, 0], [0, 3, 1, 0]]
}
```

### C#

```csharp
public class Solution {
    public void SetZeroes(int[][] matrix) {
        int m = matrix.Length;
        int n = matrix[0].Length;
        bool firstRowHasZero = false;
        bool firstColHasZero = false;

        for (int j = 0; j < n; j++) {
            if (matrix[0][j] == 0) {
                firstRowHasZero = true;
                break;
            }
        }

        for (int i = 0; i < m; i++) {
            if (matrix[i][0] == 0) {
                firstColHasZero = true;
                break;
            }
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }

        if (firstRowHasZero) {
            for (int j = 0; j < n; j++) {
                matrix[0][j] = 0;
            }
        }

        if (firstColHasZero) {
            for (int i = 0; i < m; i++) {
                matrix[i][0] = 0;
            }
        }
    }
}
```

### Java

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        boolean firstRowHasZero = false;
        boolean firstColHasZero = false;

        for (int j = 0; j < n; j++) {
            if (matrix[0][j] == 0) {
                firstRowHasZero = true;
                break;
            }
        }

        for (int i = 0; i < m; i++) {
            if (matrix[i][0] == 0) {
                firstColHasZero = true;
                break;
            }
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }

        if (firstRowHasZero) {
            for (int j = 0; j < n; j++) {
                matrix[0][j] = 0;
            }
        }

        if (firstColHasZero) {
            for (int i = 0; i < m; i++) {
                matrix[i][0] = 0;
            }
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun setZeroes(matrix: Array<IntArray>): Unit {
        val m = matrix.size
        val n = matrix[0].size
        var firstRowHasZero = false
        var firstColHasZero = false

        for (j in 0 until n) {
            if (matrix[0][j] == 0) {
                firstRowHasZero = true
                break
            }
        }

        for (i in 0 until m) {
            if (matrix[i][0] == 0) {
                firstColHasZero = true
                break
            }
        }

        for (i in 1 until m) {
            for (j in 1 until n) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0
                    matrix[0][j] = 0
                }
            }
        }

        for (i in 1 until m) {
            for (j in 1 until n) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0
                }
            }
        }

        if (firstRowHasZero) {
            for (j in 0 until n) {
                matrix[0][j] = 0
            }
        }

        if (firstColHasZero) {
            for (i in 0 until m) {
                matrix[i][0] = 0
            }
        }
    }
}
```

### Swift

```swift
class Solution {
    func setZeroes(_ matrix: inout [[Int]]) {
        let m = matrix.count
        let n = matrix[0].count
        var firstRowHasZero = false
        var firstColHasZero = false

        for j in 0..<n {
            if matrix[0][j] == 0 {
                firstRowHasZero = true
                break
            }
        }

        for i in 0..<m {
            if matrix[i][0] == 0 {
                firstColHasZero = true
                break
            }
        }

        for i in 1..<m {
            for j in 1..<n {
                if matrix[i][j] == 0 {
                    matrix[i][0] = 0
                    matrix[0][j] = 0
                }
            }
        }

        for i in 1..<m {
            for j in 1..<n {
                if matrix[i][0] == 0 || matrix[0][j] == 0 {
                    matrix[i][j] = 0
                }
            }
        }

        if firstRowHasZero {
            for j in 0..<n {
                matrix[0][j] = 0
            }
        }

        if firstColHasZero {
            for i in 0..<m {
                matrix[i][0] = 0
            }
        }
    }
}
```

### The End

