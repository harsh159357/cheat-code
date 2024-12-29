# Valid Perfect Square

## Problem Statement

Given a positive integer `num`, write a function that returns `true` if `num` is a perfect square, otherwise return `false`.

## Input

```text
num = 16
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool isPerfectSquare(int num) {
  int left = 1;
  int right = num;

  while (left <= right) {
    int mid = left + (right - left) ~/ 2;
    int square = mid * mid;

    if (square == num) {
      return true;
    } else if (square < num) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }

  return false;
}
```

### C#

```csharp
public class Solution {
    public bool IsPerfectSquare(int num) {
        long left = 1, right = num;
        while (left <= right) {
            long mid = left + (right - left) / 2;
            long square = mid * mid;
            if (square == num) {
                return true;
            } else if (square < num) {
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
    public boolean isPerfectSquare(int num) {
        long left = 1, right = num;
        while (left <= right) {
            long mid = left + (right - left) / 2;
            long square = mid * mid;
            if (square == num) {
                return true;
            } else if (square < num) {
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
    fun isPerfectSquare(num: Int): Boolean {
        var left = 1L
        var right = num.toLong()

        while (left <= right) {
            val mid = left + (right - left) / 2
            val square = mid * mid

            if (square == num.toLong()) {
                return true
            } else if (square < num) {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return false
    }
}
```

### Swift

```swift
class Solution {
    func isPerfectSquare(_ num: Int) -> Bool {
        var left: Int64 = 1
        var right: Int64 = Int64(num)

        while left <= right {
            let mid = left + (right - left) / 2
            let square = mid * mid

            if square == num {
                return true
            } else if square < num {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return false
    }
}
```


### The End

