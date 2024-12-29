# Bitwise AND of Numbers Range

## Problem Statement

Given two integers `left` and `right` that represent the range `[left, right]`, return the bitwise AND of all numbers in this range, inclusive.

## Input

```text
left = 5
right = 7
```

## Output

```text
4
```

## Solutions

### Dart

```dart
int rangeBitwiseAnd(int left, int right) {
  if (left == 0 || right == 0) {
    return 0;
  }

  int mask = 0x7FFFFFFF;
  while ((left & mask) != (right & mask)) {
    mask <<= 1;
    mask &= 0x7FFFFFFF;
  }
  return right & mask;
}
```

### C#

```csharp
public class Solution {
    public int RangeBitwiseAnd(int left, int right) {
        if (left == 0 || right == 0) return 0;

        int mask = 0x7FFFFFFF;
        while ((left & mask) != (right & mask)) {
            mask <<= 1;
            mask &= 0x7FFFFFFF;
        }
        return right & mask;
    }
}
```

### Java

```java
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
        if (left == 0 || right == 0) return 0;

        int mask = 0x7FFFFFFF;
        while ((left & mask) != (right & mask)) {
            mask <<= 1;
            mask &= 0x7FFFFFFF;
        }
        return right & mask;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun rangeBitwiseAnd(left: Int, right: Int): Int {
        if (left == 0 || right == 0) {
            return 0
        }

        var mask = 0x7FFFFFFF
        while ((mask and left) != (mask and right)) {
            mask = mask shl 1
            mask = mask and 0x7FFFFFFF
        }
        return right and mask
    }
}
```

### Swift

```swift
class Solution {
    func rangeBitwiseAnd(_ left: Int, _ right: Int) -> Int {
        if left == 0 || right == 0 {
            return 0
        }

        var mask = 0x7FFFFFFF
        var l = left
        var r = right

        while (mask & l) != (mask & r) {
            mask = mask << 1
            mask = mask & 0x7FFFFFFF
        }
        return r & mask
    }
}
```


### The End

