# Domino and Tromino Tiling

## Problem Statement

You have a 2 x n board and you want to cover the entire board using:

1. Domino pieces, which are 2 x 1 or 1 x 2 rectangles.
2. Tromino pieces, which are "L" shaped 2 x 2 - 1 blocks.

Return the number of ways to tile the board. Since the answer may be very large, return it modulo \(10^9 + 7\).

## Input

```text
n = 3
```

## Output

```text
5
```


## Solutions

### Dart

```dart
int numTilings(int n) {
  if (n < 3) return n;

  List<int> array = [1, 2, 5];
  for (int i = 3; i < n; i++) {
    int temp = array[0];
    array[0] = array[1];
    array[1] = array[2];
    array[2] = ((array[2] * 2 + temp) % 1000000007);
  }
  return array[2];
}
```

### C#

```csharp
public class Solution {
    public int NumTilings(int n) {
        if (n < 3) return n;

        long[] array = { 1, 2, 5 };
        for (int i = 3; i < n; i++) {
            long temp = array[0];
            array[0] = array[1];
            array[1] = array[2];
            array[2] = (array[2] * 2 + temp) % 1000000007;
        }

        return (int)array[2];
    }
}
```

### Java

```java
class Solution {
    public int numTilings(int n) {
        if (n < 3) return n;

        long[] array = {1, 2, 5};
        for (int i = 3; i < n; i++) {
            long temp = array[0];
            array[0] = array[1];
            array[1] = array[2];
            array[2] = (array[2] * 2 + temp) % 1000000007;
        }

        return (int) array[2];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun numTilings(n: Int): Int {
        if (n < 3) return n

        var array = longArrayOf(1, 2, 5)
        for (i in 3 until n) {
            val temp = array[0]
            array[0] = array[1]
            array[1] = array[2]
            array[2] = ((array[2] * 2 + temp) % 1000000007)
        }
        return array[2].toInt()
    }
}
```

### Swift

```swift
class Solution {
    func numTilings(_ n: Int) -> Int {
        if n < 3 { return n }

        var array: [Int] = [1, 2, 5]
        for _ in 3..<n {
            let temp = array[0]
            array[0] = array[1]
            array[1] = array[2]
            array[2] = (array[2] * 2 + temp) % 1000000007
        }

        return array[2]
    }
}
```


### The End