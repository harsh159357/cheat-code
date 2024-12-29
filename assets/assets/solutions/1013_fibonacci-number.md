# Fibonacci Number

## Problem Statement

The Fibonacci numbers, commonly denoted as `F(n)`, form a sequence such that:
- `F(0) = 0`, `F(1) = 1`, and
- `F(n) = F(n - 1) + F(n - 2)` for `n > 1`.

Given `n`, calculate `F(n)`.

## Input

```text
n = 4
```

## Output

```text
3
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun fib(n: Int): Int {
        if (n <= 1) return n

        var prev1 = 0
        var prev2 = 1

        for (i in 2..n) {
            val current = prev1 + prev2
            prev1 = prev2
            prev2 = current
        }

        return prev2
    }
}

fun main() {
    val solution = Solution()
    println(solution.fib(4)) // Output: 3
}
```


### Dart

```dart
int fib(int n) {
  if (n <= 1) return n;

  int prev1 = 0, prev2 = 1;

  for (int i = 2; i <= n; i++) {
    int current = prev1 + prev2;
    prev1 = prev2;
    prev2 = current;
  }

  return prev2;
}

void main() {
  print(fib(4)); // Output: 3
}
```


### C#

```csharp
public class Solution {
    public int Fib(int n) {
        if (n <= 1) return n;

        int prev1 = 0, prev2 = 1;

        for (int i = 2; i <= n; i++) {
            int current = prev1 + prev2;
            prev1 = prev2;
            prev2 = current;
        }

        return prev2;
    }
}
```


### Java

```java
class Solution {
    public int fib(int n) {
        if (n <= 1) return n;

        int prev1 = 0, prev2 = 1;

        for (int i = 2; i <= n; i++) {
            int current = prev1 + prev2;
            prev1 = prev2;
            prev2 = current;
        }

        return prev2;
    }
}
```


### Swift

```swift
class Solution {
    func fib(_ n: Int) -> Int {
        if n <= 1 { return n }

        var prev1 = 0, prev2 = 1

        for _ in 2...n {
            let current = prev1 + prev2
            prev1 = prev2
            prev2 = current
        }

        return prev2
    }
}

let solution = Solution()
print(solution.fib(4)) // Output: 3
```


### The End