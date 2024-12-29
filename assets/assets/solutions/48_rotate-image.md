# Rotate Image

## Problem Statement

You are given an `n x n` 2D matrix representing an image. Rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

## Input

```text
matrix = [
[1, 2, 3],
[4, 5, 6],
[7, 8, 9]
]
```

## Output

```text
[
[7, 4, 1],
[8, 5, 2],
[9, 6, 3]
]  
(Explanation: The matrix is rotated 90 degrees clockwise.)
```

## Solutions

### Dart

```dart
void rotate(List<List<int>> matrix) {
  int n = matrix.length;

  // Transpose the matrix
  for (int i = 0; i < n; i++) {
    for (int j = i; j < n; j++) {
      int temp = matrix[i][j];
      matrix[i][j] = matrix[j][i];
      matrix[j][i] = temp;
    }
  }

  // Reverse each row
  for (int i = 0; i < n; i++) {
    int left = 0;
    int right = n - 1;
    while (left < right) {
      int temp = matrix[i][left];
      matrix[i][left] = matrix[i][right];
      matrix[i][right] = temp;
      left++;
      right--;
    }
  }
}

void main() {
  List<List<int>> matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
  ];
  rotate(matrix);
  print(matrix); // Output: [[7, 4, 1], [8, 5, 2], [9, 6, 3]]
}
```

### C#

```csharp
public class Solution {
    public void Rotate(int[][] matrix) {
        int n = matrix.Length;

        // Transpose the matrix
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        // Reverse each row
        for (int i = 0; i < n; i++) {
            int left = 0, right = n - 1;
            while (left < right) {
                int temp = matrix[i][left];
                matrix[i][left] = matrix[i][right];
                matrix[i][right] = temp;
                left++;
                right--;
            }
        }
    }
}
```

### Java

```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;

        // Transpose the matrix
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        // Reverse each row
        for (int i = 0; i < n; i++) {
            int left = 0, right = n - 1;
            while (left < right) {
                int temp = matrix[i][left];
                matrix[i][left] = matrix[i][right];
                matrix[i][right] = temp;
                left++;
                right--;
            }
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun rotate(matrix: Array<IntArray>) {
        val n = matrix.size

        // Transpose the matrix
        for (i in 0 until n) {
            for (j in i until n) {
                val temp = matrix[i][j]
                matrix[i][j] = matrix[j][i]
                matrix[j][i] = temp
            }
        }

        // Reverse each row
        for (i in 0 until n) {
            var left = 0
            var right = n - 1
            while (left < right) {
                val temp = matrix[i][left]
                matrix[i][left] = matrix[i][right]
                matrix[i][right] = temp
                left++
                right--
            }
        }
    }
}
```

### Swift

```swift
class Solution {
    func rotate(_ matrix: inout [[Int]]) {
        let n = matrix.count

        // Transpose the matrix
        for i in 0..<n {
            for j in i..<n {
                let temp = matrix[i][j]
                matrix[i][j] = matrix[j][i]
                matrix[j][i] = temp
            }
        }

        // Reverse each row
        for i in 0..<n {
            var left = 0
            var right = n - 1
            while left < right {
                let temp = matrix[i][left]
                matrix[i][left] = matrix[i][right]
                matrix[i][right] = temp
                left += 1
                right -= 1
            }
        }
    }
}

var matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
let solution = Solution()
solution.rotate(&matrix)
print(matrix) // Output: [[7, 4, 1], [8, 5, 2], [9, 6, 3]]
```


### The End

