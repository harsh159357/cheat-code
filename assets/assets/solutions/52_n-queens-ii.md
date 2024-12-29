# N-Queens II

## Problem Statement

The `n`-queens puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return the number of distinct solutions to the `n`-queens puzzle.

## Input

```text
n = 4
```

## Output

```text
2  
(Explanation: There are two distinct solutions for the 4-queens puzzle.)
```

## Solutions

### Dart

```dart
int totalNQueens(int n) {
  List<bool> col = List.filled(n, false);
  List<bool> diag1 = List.filled(2 * n - 1, false);
  List<bool> diag2 = List.filled(2 * n - 1, false);

  int backtrack(int row) {
    if (row == n) return 1;
    int count = 0;
    for (int i = 0; i < n; i++) {
      if (col[i] || diag1[row + i] || diag2[row - i + n - 1]) continue;
      col[i] = true;
      diag1[row + i] = true;
      diag2[row - i + n - 1] = true;
      count += backtrack(row + 1);
      col[i] = false;
      diag1[row + i] = false;
      diag2[row - i + n - 1] = false;
    }
    return count;
  }

  return backtrack(0);
}

void main() {
  print(totalNQueens(4)); // Output: 2
}
```

### C#

```csharp
public class Solution {
    public int TotalNQueens(int n) {
        bool[] col = new bool[n];
        bool[] diag1 = new bool[2 * n - 1];
        bool[] diag2 = new bool[2 * n - 1];

        int Backtrack(int row) {
            if (row == n) return 1;
            int count = 0;
            for (int i = 0; i < n; i++) {
                if (col[i] || diag1[row + i] || diag2[row - i + n - 1]) continue;
                col[i] = true;
                diag1[row + i] = true;
                diag2[row - i + n - 1] = true;
                count += Backtrack(row + 1);
                col[i] = false;
                diag1[row + i] = false;
                diag2[row - i + n - 1] = false;
            }
            return count;
        }

        return Backtrack(0);
    }
}
```

### Java

```java
class Solution {
    public int totalNQueens(int n) {
        boolean[] col = new boolean[n];
        boolean[] diag1 = new boolean[2 * n - 1];
        boolean[] diag2 = new boolean[2 * n - 1];

        return backtrack(0);

        int backtrack(int row) {
            if (row == n) return 1;
            int count = 0;
            for (int i = 0; i < n; i++) {
                if (col[i] || diag1[row + i] || diag2[row - i + n - 1]) continue;
                col[i] = true;
                diag1[row + i] = true;
                diag2[row - i + n - 1] = true;
                count += backtrack(row + 1);
                col[i] = false;
                diag1[row + i] = false;
                diag2[row - i + n - 1] = false;
            }
            return count;
        }

        return backtrack(0);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun totalNQueens(n: Int): Int {
        val col = BooleanArray(n)
        val diag1 = BooleanArray(2 * n - 1)
        val diag2 = BooleanArray(2 * n - 1)

        fun backtrack(row: Int): Int {
            if (row == n) return 1
            var count = 0
            for (i in 0 until n) {
                if (col[i] || diag1[row + i] || diag2[row - i + n - 1]) continue
                col[i] = true
                diag1[row + i] = true
                diag2[row - i + n - 1] = true
                count += backtrack(row + 1)
                col[i] = false
                diag1[row + i] = false
                diag2[row - i + n - 1] = false
            }
            return count
        }

        return backtrack(0)
    }
}
```

### Swift

```swift
class Solution {
    func totalNQueens(_ n: Int) -> Int {
        var col = Array(repeating: false, count: n)
        var diag1 = Array(repeating: false, count: 2 * n - 1)
        var diag2 = Array(repeating: false, count: 2 * n - 1)

        func backtrack(_ row: Int) -> Int {
            if row == n { return 1 }
            var count = 0
            for i in 0..<n {
                if col[i] || diag1[row + i] || diag2[row - i + n - 1] { continue }
                col[i] = true
                diag1[row + i] = true
                diag2[row - i + n - 1] = true
                count += backtrack(row + 1)
                col[i] = false
                diag1[row + i] = false
                diag2[row - i + n - 1] = false
            }
            return count
        }

        return backtrack(0)
    }
}

let solution = Solution()
print(solution.totalNQueens(4)) // Output: 2
```

### The End

