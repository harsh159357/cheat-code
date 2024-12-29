# N-th Tribonacci Number

## Problem Statement

The Tribonacci sequence is defined as follows:

- `T0 = 0`, `T1 = 1`, `T2 = 1`
- `Tn+3 = Tn + Tn+1 + Tn+2` for `n >= 0`.

Given `n`, return the value of `Tn`.

## Input

```text
n = 4
```

## Output

```text
4
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun tribonacci(n: Int): Int {
        if (n == 0) return 0
        if (n == 1 || n == 2) return 1
        var a = 0
        var b = 1
        var c = 1
        for (i in 3..n) {
            val temp = a + b + c
            a = b
            b = c
            c = temp
        }
        return c
    }
}
```

### Dart

```dart
int tribonacci(int n) {
  if (n == 0) return 0;
  if (n == 1 || n == 2) return 1;

  int a = 0, b = 1, c = 1;

  for (int i = 3; i <= n; i++) {
    int temp = a + b + c;
    a = b;
    b = c;
    c = temp;
  }

  return c;
}
```

### C#

```csharp
public class Solution {
    public int Tribonacci(int n) {
        if (n == 0) return 0;
        if (n == 1 || n == 2) return 1;

        int a = 0, b = 1, c = 1;

        for (int i = 3; i <= n; i++) {
            int temp = a + b + c;
            a = b;
            b = c;
            c = temp;
        }

        return c;
    }
}
```

### Java

```java
class Solution {
    public int tribonacci(int n) {
        if (n == 0) return 0;
        if (n == 1 || n == 2) return 1;

        int a = 0, b = 1, c = 1;

        for (int i = 3; i <= n; i++) {
            int temp = a + b + c;
            a = b;
            b = c;
            c = temp;
        }

        return c;
    }
}
```

### Swift

```swift
class Solution {
    func tribonacci(_ n: Int) -> Int {
        if n == 0 { return 0 }
        if n == 1 || n == 2 { return 1 }

        var a = 0, b = 1, c = 1

        for _ in 3...n {
            let temp = a + b + c
            a = b
            b = c
            c = temp
        }

        return c
    }
}
```

### The End