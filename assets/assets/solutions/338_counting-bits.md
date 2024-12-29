# Counting Bits

## Problem Statement

Given an integer `num`, return an array `ans` where `ans[i]` is the number of `1`s in the binary representation of `i` for each `0 <= i <= num`.

## Input

```text
num = 5
```

## Output

```text
[0, 1, 1, 2, 1, 2]
```

## Solutions

### Dart

```dart
List<int> countBits(int num) {
  List<int> bits = List.filled(num + 1, 0);
  for (int i = 1; i <= num; i++) {
    bits[i] = bits[i >> 1] + (i & 1);
  }
  return bits;
}
```

### C#

```csharp
public class Solution {
    public int[] CountBits(int num) {
        int[] bits = new int[num + 1];
        for (int i = 1; i <= num; i++) {
            bits[i] = bits[i >> 1] + (i & 1);
        }
        return bits;
    }
}
```

### Java

```java
class Solution {
    public int[] countBits(int num) {
        int[] bits = new int[num + 1];
        for (int i = 1; i <= num; i++) {
            bits[i] = bits[i >> 1] + (i & 1);
        }
        return bits;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun countBits(num: Int): IntArray {
        val bits = IntArray(num + 1)
        for (i in 1..num) {
            bits[i] = bits[i shr 1] + (i and 1)
        }
        return bits
    }
}
```

### Swift

```swift
class Solution {
    func countBits(_ num: Int) -> [Int] {
        var bits = [Int](repeating: 0, count: num + 1)
        for i in 1...num {
            bits[i] = bits[i >> 1] + (i & 1)
        }
        return bits
    }
}
```


### The End

