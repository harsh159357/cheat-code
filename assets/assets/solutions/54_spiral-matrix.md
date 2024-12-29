# Spiral Matrix

## Problem Statement

Given an `m x n` matrix, return all elements of the matrix in spiral order.

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
[1, 2, 3, 6, 9, 8, 7, 4, 5]  
(Explanation: The elements are traversed in spiral order.)
```

## Solutions

### Dart

```dart
List<int> spiralOrder(List<List<int>> matrix) {
  List<int> result = [];
  int top = 0, bottom = matrix.length - 1;
  int left = 0, right = matrix[0].length - 1;

  while (top <= bottom && left <= right) {
    for (int i = left; i <= right; i++) {
      result.add(matrix[top][i]);
    }
    top++;

    for (int i = top; i <= bottom; i++) {
      result.add(matrix[i][right]);
    }
    right--;

    if (top <= bottom) {
      for (int i = right; i >= left; i--) {
        result.add(matrix[bottom][i]);
      }
      bottom--;
    }

    if (left <= right) {
      for (int i = bottom; i >= top; i--) {
        result.add(matrix[i][left]);
      }
      left++;
    }
  }

  return result;
}

void main() {
  print(spiralOrder([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
  ])); // Output: [1, 2, 3, 6, 9, 8, 7, 4, 5]
}
```

### C#

```csharp
public class Solution {
    public IList<int> SpiralOrder(int[][] matrix) {
        List<int> result = new List<int>();
        int top = 0, bottom = matrix.Length - 1;
        int left = 0, right = matrix[0].Length - 1;

        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++) {
                result.Add(matrix[top][i]);
            }
            top++;

            for (int i = top; i <= bottom; i++) {
                result.Add(matrix[i][right]);
            }
            right--;

            if (top <= bottom) {
                for (int i = right; i >= left; i--) {
                    result.Add(matrix[bottom][i]);
                }
                bottom--;
            }

            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    result.Add(matrix[i][left]);
                }
                left++;
            }
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<>();
        int top = 0, bottom = matrix.length - 1;
        int left = 0, right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++) {
                result.add(matrix[top][i]);
            }
            top++;

            for (int i = top; i <= bottom; i++) {
                result.add(matrix[i][right]);
            }
            right--;

            if (top <= bottom) {
                for (int i = right; i >= left; i--) {
                    result.add(matrix[bottom][i]);
                }
                bottom--;
            }

            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    result.add(matrix[i][left]);
                }
                left++;
            }
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun spiralOrder(matrix: Array<IntArray>): List<Int> {
        val result = mutableListOf<Int>()

        var top = 0
        var bottom = matrix.size - 1
        var left = 0
        var right = matrix[0].size - 1

        while (top <= bottom && left <= right) {
            for (col in left..right) {
                result.add(matrix[top][col])
            }
            top++

            for (row in top..bottom) {
                result.add(matrix[row][right])
            }
            right--

            if (top <= bottom) {
                for (col in right downTo left) {
                    result.add(matrix[bottom][col])
                }
                bottom--
            }

            if (left <= right) {
                for (row in bottom downTo top) {
                    result.add(matrix[row][left])
                }
                left++
            }
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func spiralOrder(_ matrix: [[Int]]) -> [Int] {
        var result = [Int]()
        var top = 0, bottom = matrix.count - 1
        var left = 0, right = matrix[0].count - 1

        while top <= bottom && left <= right {
            for col in left...right {
                result.append(matrix[top][col])
            }
            top += 1

            for row in top...bottom {
                result.append(matrix[row][right])
            }
            right -= 1

            if top <= bottom {
                for col in stride(from: right, through: left, by: -1) {
                    result.append(matrix[bottom][col])
                }
                bottom -= 1
            }

            if left <= right {
                for row in stride(from: bottom, through: top, by: -1) {
                    result.append(matrix[row][left])
                }
                left += 1
            }
        }

        return result
    }
}

let solution = Solution()
print(solution.spiralOrder([[1, 2, 3], [4, 5, 6], [7, 8, 9]])) // Output: [1, 2, 3, 6, 9, 8, 7, 4, 5]
```

### The End

