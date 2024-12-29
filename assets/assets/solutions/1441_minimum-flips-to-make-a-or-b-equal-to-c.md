# Minimum Flips to Make A OR B Equal to C

## Problem Statement

Given three integers `a`, `b`, and `c`, you can flip any bit (change `0` to `1` or `1` to `0`) in `a` or `b`. Return the minimum number of flips required in some bits of `a` or `b` such that `a OR b == c`.

## Input

```text
a = 2, b = 6, c = 5
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun minFlips(a: Int, b: Int, c: Int): Int {
        var flips = 0
        var aa = a
        var bb = b
        var cc = c

        while (aa > 0 || bb > 0 || cc > 0) {
            val bitA = aa and 1
            val bitB = bb and 1
            val bitC = cc and 1

            if (bitC == 0) {
                if (bitA == 1) flips++
                if (bitB == 1) flips++
            } else {
                if (bitA == 0 && bitB == 0) flips++
            }

            aa = aa shr 1
            bb = bb shr 1
            cc = cc shr 1
        }

        return flips
    }
}
```

### Dart

```dart
int minFlips(int a, int b, int c) {
  int flips = 0;

  while (a > 0 || b > 0 || c > 0) {
    int bitA = a & 1;
    int bitB = b & 1;
    int bitC = c & 1;

    if (bitC == 0) {
      if (bitA == 1) flips++;
      if (bitB == 1) flips++;
    } else {
      if (bitA == 0 && bitB == 0) flips++;
    }

    a >>= 1;
    b >>= 1;
    c >>= 1;
  }

  return flips;
}
```

### C#

```csharp
public class Solution {
    public int MinFlips(int a, int b, int c) {
        int flips = 0;

        while (a > 0 || b > 0 || c > 0) {
            int bitA = a & 1;
            int bitB = b & 1;
            int bitC = c & 1;

            if (bitC == 0) {
                if (bitA == 1) flips++;
                if (bitB == 1) flips++;
            } else {
                if (bitA == 0 && bitB == 0) flips++;
            }

            a >>= 1;
            b >>= 1;
            c >>= 1;
        }

        return flips;
    }
}
```

### Java

```java
class Solution {
    public int minFlips(int a, int b, int c) {
        int flips = 0;

        while (a > 0 || b > 0 || c > 0) {
            int bitA = a & 1;
            int bitB = b & 1;
            int bitC = c & 1;

            if (bitC == 0) {
                if (bitA == 1) flips++;
                if (bitB == 1) flips++;
            } else {
                if (bitA == 0 && bitB == 0) flips++;
            }

            a >>= 1;
            b >>= 1;
            c >>= 1;
        }

        return flips;
    }
}
```

### Swift

```swift
class Solution {
    func minFlips(_ a: Int, _ b: Int, _ c: Int) -> Int {
        var flips = 0
        var aa = a
        var bb = b
        var cc = c

        while aa > 0 || bb > 0 || cc > 0 {
            let bitA = aa & 1
            let bitB = bb & 1
            let bitC = cc & 1

            if bitC == 0 {
                if bitA == 1 { flips += 1 }
                if bitB == 1 { flips += 1 }
            } else {
                if bitA == 0 && bitB == 0 { flips += 1 }
            }

            aa >>= 1
            bb >>= 1
            cc >>= 1
        }

        return flips
    }
}
```

### The End