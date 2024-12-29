# Arranging Coins

## Problem Statement

You have `n` coins, and you want to build a staircase with them. The staircase consists of `k` rows where the `i-th` row has exactly `i` coins. The last row may be incomplete.

Return the number of complete rows that can be formed.

## Input

```text
n = 8
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int arrangeCoins(int n) {
  int left = 0;
  int right = n;

  while (left <= right) {
    int mid = left + (right - left) ~/ 2;
    int coinsInRows = mid * (mid + 1) ~/ 2;

    if (coinsInRows == n) {
      return mid; // Exact number of coins to form rows
    } else if (coinsInRows < n) {
      left = mid + 1; // More rows can be formed, search in the right half
    } else {
      right = mid - 1; // Less rows need to be formed, search in the left half
    }
  }

  return right; // Return the maximum number of complete rows
}
```

### C#

```csharp
public class Solution {
    public int ArrangeCoins(int n) {
        long left = 0, right = n;

        while (left <= right) {
            long mid = left + (right - left) / 2;
            long coinsInRows = (mid * (mid + 1)) / 2;

            if (coinsInRows == n) {
                return (int)mid; // Exact number of coins to form rows
            } else if (coinsInRows < n) {
                left = mid + 1; // More rows can be formed
            } else {
                right = mid - 1; // Less rows need to be formed
            }
        }

        return (int)right; // Return the maximum number of complete rows
    }
}
```

### Java

```java
class Solution {
    public int arrangeCoins(int n) {
        long left = 0, right = n;

        while (left <= right) {
            long mid = left + (right - left) / 2;
            long coinsInRows = mid * (mid + 1) / 2;

            if (coinsInRows == n) {
                return (int)mid; // Exact number of coins to form rows
            } else if (coinsInRows < n) {
                left = mid + 1; // More rows can be formed
            } else {
                right = mid - 1; // Less rows need to be formed
            }
        }

        return (int)right; // Return the maximum number of complete rows
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun arrangeCoins(n: Int): Int {
        var left = 0L
        var right = n.toLong()

        while (left <= right) {
            val mid = left + (right - left) / 2
            val coinsInRows = (mid * (mid + 1)) / 2

            if (coinsInRows == n.toLong()) {
                return mid.toInt() // Exact number of coins to form rows
            } else if (coinsInRows < n) {
                left = mid + 1 // More rows can be formed
            } else {
                right = mid - 1 // Less rows need to be formed
            }
        }

        return right.toInt() // Return the maximum number of complete rows
    }
}

fun main() {
    val n = 8
    println(Solution().arrangeCoins(n)) // Output: 3
}
```

### Swift

```swift
class Solution {
    func arrangeCoins(_ n: Int) -> Int {
        var left: Int64 = 0
        var right: Int64 = Int64(n)

        while left <= right {
            let mid = left + (right - left) / 2
            let coinsInRows = mid * (mid + 1) / 2

            if coinsInRows == n {
                return Int(mid) // Exact number of coins to form rows
            } else if coinsInRows < n {
                left = mid + 1 // More rows can be formed
            } else {
                right = mid - 1 // Less rows need to be formed
            }
        }

        return Int(right) // Return the maximum number of complete rows
    }
}
```

### The End