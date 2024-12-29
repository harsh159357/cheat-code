# Search a 2D Matrix

## Problem Statement

Write an efficient algorithm that searches for a value in an `m x n` matrix. This matrix has the following properties:

- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

## Input

```text
matrix = [  
[1, 3, 5, 7],  
[10, 11, 16, 20],  
[23, 30, 34, 60]  
]  
target = 3
```

## Output

```text
`true`

(Explanation: The target value 3 is found in the matrix.)
```

## Solutions

### Dart

```dart
bool searchMatrix(List<List<int>> matrix, int target) {
  if (matrix.isEmpty || matrix[0].isEmpty) return false;
  int m = matrix.length;
  int n = matrix[0].length;
  int left = 0;
  int right = m * n - 1;

  while (left <= right) {
    int mid = left + (right - left) ~/ 2;
    int num = matrix[mid ~/ n][mid % n];

    if (num == target) {
      return true;
    } else if (num < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return false;
}

void main() {
  var matrix = [
    [1, 3, 5, 7],
    [10, 11, 16, 20],
    [23, 30, 34, 60]
  ];
  print(searchMatrix(matrix, 3)); // Output: true
  print(searchMatrix(matrix, 13)); // Output: false
}
```

### C#

```csharp
public class Solution {
    public bool SearchMatrix(int[][] matrix, int target) {
        if (matrix.Length == 0 || matrix[0].Length == 0) return false;

        int m = matrix.Length;
        int n = matrix[0].Length;
        int left = 0;
        int right = m * n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int num = matrix[mid / n][mid % n];

            if (num == target) {
                return true;
            } else if (num < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
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

        int m = matrix.length;
        int n = matrix[0].length;
        int left = 0;
        int right = m * n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int num = matrix[mid / n][mid % n];

            if (num == target) {
                return true;
            } else if (num < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
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
        val m = matrix.size
        val n = matrix[0].size
        var left = 0
        var right = m * n - 1

        while (left <= right) {
            val mid = left + (right - left) / 2
            val num = matrix[mid / n][mid % n]

            if (num == target) return true
            if (num < target) left = mid + 1
            else right = mid - 1
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

        let m = matrix.count
        let n = matrix[0].count
        var left = 0
        var right = m * n - 1

        while left <= right {
            let mid = left + (right - left) / 2
            let num = matrix[mid / n][mid % n]

            if num == target {
                return true
            } else if num < target {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }
        return false
    }
}

let solution = Solution()
print(solution.searchMatrix([[1, 3, 5, 7], [10, 11, 16, 20], [23, 30, 34, 60]], 3)) // Output: true
print(solution.searchMatrix([[1, 3, 5, 7], [10, 11, 16, 20], [23, 30, 34, 60]], 13)) // Output: false
```

### The End

