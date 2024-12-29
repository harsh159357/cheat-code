# Matrix Diagonal Sum

## Problem Statement

Given a square matrix `mat`, return the sum of the matrix diagonals. Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal.

## Input

```text
mat = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

## Output

```text
25
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun diagonalSum(mat: Array<IntArray>): Int {
        val n = mat.size
        var sum = 0

        for (i in 0 until n) {
            sum += mat[i][i] // Add main diagonal element
            sum += mat[i][n - 1 - i] // Add secondary diagonal element
        }

        // If matrix size is odd, subtract the middle element counted twice
        if (n % 2 != 0) {
            sum -= mat[n / 2][n / 2]
        }

        return sum
    }
}

fun main() {
    val mat = arrayOf(
        intArrayOf(1, 2, 3),
        intArrayOf(4, 5, 6),
        intArrayOf(7, 8, 9)
    )
    println(Solution().diagonalSum(mat)) // Output: 25
}
```

### Dart

```dart
int diagonalSum(List<List<int>> mat) {
  int n = mat.length;
  int sum = 0;

  for (int i = 0; i < n; i++) {
    sum += mat[i][i]; // Add main diagonal element
    sum += mat[i][n - 1 - i]; // Add secondary diagonal element
  }

  // If matrix size is odd, subtract the middle element counted twice
  if (n % 2 != 0) {
    sum -= mat[n ~/ 2][n ~/ 2];
  }

  return sum;
}

void main() {
  List<List<int>> mat = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
  ];
  print(diagonalSum(mat)); // Output: 25
}
```

### C#

```csharp
public class Solution {
    public int DiagonalSum(int[][] mat) {
        int n = mat.Length;
        int sum = 0;

        for (int i = 0; i < n; i++) {
            sum += mat[i][i]; // Add main diagonal element
            sum += mat[i][n - 1 - i]; // Add secondary diagonal element
        }

        // If matrix size is odd, subtract the middle element counted twice
        if (n % 2 != 0) {
            sum -= mat[n / 2][n / 2];
        }

        return sum;
    }
}
```

### Java

```java
class Solution {
    public int diagonalSum(int[][] mat) {
        int n = mat.length;
        int sum = 0;

        for (int i = 0; i < n; i++) {
            sum += mat[i][i]; // Add main diagonal element
            sum += mat[i][n - 1 - i]; // Add secondary diagonal element
        }

        // If matrix size is odd, subtract the middle element counted twice
        if (n % 2 != 0) {
            sum -= mat[n / 2][n / 2];
        }

        return sum;
    }
}
```

### Swift

```swift
class Solution {
    func diagonalSum(_ mat: [[Int]]) -> Int {
        let n = mat.count
        var sum = 0

        for i in 0..<n {
            sum += mat[i][i] // Add main diagonal element
            sum += mat[i][n - 1 - i] // Add secondary diagonal element
        }

        // If matrix size is odd, subtract the middle element counted twice
        if n % 2 != 0 {
            sum -= mat[n / 2][n / 2]
        }

        return sum
    }
}

let mat = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print(Solution().diagonalSum(mat)) // Output: 25
```

### The End