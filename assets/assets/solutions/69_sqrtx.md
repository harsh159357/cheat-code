# Square Root (x)

## Problem Statement

Given a non-negative integer `x`, compute and return the square root of `x`. Since the return type is an integer, the decimal digits are truncated, and only the integer part of the result is returned.

## Input

```text
x = 8
```

## Output

```text
2  
(Explanation: The square root of 8 is approximately 2.82842. Since the return type is an integer, the decimal part is truncated.)
```

## Solutions

### Dart

```dart
int mySqrt(int x) {
  int left = 0;
  int right = x;

  while (left <= right) {
    int mid = left + (right - left) ~/ 2;
    int square = mid * mid;

    if (square == x) return mid;
    if (square < x) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }

  return right;
}

void main() {
  print(mySqrt(8)); // Output: 2
  print(mySqrt(16)); // Output: 4
}
```

### C#

```csharp
public class Solution {
    public int MySqrt(int x) {
        int left = 0, right = x;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            long square = (long)mid * mid;

            if (square == x) return mid;
            if (square < x) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return right;
    }
}
```

### Java

```java
class Solution {
    public int mySqrt(int x) {
        int left = 0, right = x;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            long square = (long) mid * mid;

            if (square == x) return mid;
            if (square < x) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return right;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun mySqrt(x: Int): Int {
        var left = 0
        var right = x

        while (left <= right) {
            val mid = left + (right - left) / 2
            val square = mid.toLong() * mid

            if (square == x.toLong()) return mid
            if (square < x) {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return right
    }
}
```

### Swift

```swift
class Solution {
    func mySqrt(_ x: Int) -> Int {
        var left = 0
        var right = x

        while left <= right {
            let mid = left + (right - left) / 2
            let square = mid * mid

            if square == x {
                return mid
            } else if square < x {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return right
    }
}

let solution = Solution()
print(solution.mySqrt(8)) // Output: 2
print(solution.mySqrt(16)) // Output: 4
```

### The End

