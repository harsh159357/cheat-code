# Pow(x, n)

## Problem Statement

Implement `pow(x, n)`, which calculates `x` raised to the power `n` (`x^n`).

## Input

```text
x = 2.0, n = 10
```

## Output

```text
1024.0  
(Explanation: `2.0^10 = 1024.0`.)
```

## Solutions

### Dart

```dart
double myPow(double x, int n) {
  if (n == 0) return 1.0;
  double result = 1.0;
  long power = n;
  if (power < 0) {
    x = 1 / x;
    power = -power;
  }

  while (power > 0) {
    if (power % 2 == 1) result *= x;
    x *= x;
    power ~/= 2;
  }
  return result;
}

void main() {
  print(myPow(2.0, 10)); // Output: 1024.0
  print(myPow(2.1, 3)); // Output: 9.261
  print(myPow(2.0, -2)); // Output: 0.25
}
```

### C#

```csharp
public class Solution {
    public double MyPow(double x, int n) {
        if (n == 0) return 1.0;
        double result = 1.0;
        long power = n;
        if (power < 0) {
            x = 1 / x;
            power = -power;
        }

        while (power > 0) {
            if (power % 2 == 1) result *= x;
            x *= x;
            power /= 2;
        }
        return result;
    }
}
```

### Java

```java
class Solution {
    public double myPow(double x, int n) {
        if (n == 0) return 1.0;
        double result = 1.0;
        long power = n;
        if (power < 0) {
            x = 1 / x;
            power = -power;
        }

        while (power > 0) {
            if (power % 2 == 1) result *= x;
            x *= x;
            power /= 2;
        }
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun myPow(x: Double, n: Int): Double {
        if (n == 0) return 1.0
        var result = 1.0
        var power = n.toLong()
        var base = x
        if (power < 0) {
            base = 1 / base
            power = -power
        }
        while (power > 0) {
            if (power % 2 == 1L) result *= base
            base *= base
            power /= 2
        }
        return result
    }
}
```

### Swift

```swift
class Solution {
    func myPow(_ x: Double, _ n: Int) -> Double {
        if n == 0 { return 1.0 }
        var result = 1.0
        var base = x
        var power = n
        if power < 0 {
            base = 1 / base
            power = -power
        }

        while power > 0 {
            if power % 2 == 1 {
                result *= base
            }
            base *= base
            power /= 2
        }

        return result
    }
}

let solution = Solution()
print(solution.myPow(2.0, 10)) // Output: 1024.0
print(solution.myPow(2.1, 3)) // Output: 9.261
print(solution.myPow(2.0, -2)) // Output: 0.25
```

### The End

