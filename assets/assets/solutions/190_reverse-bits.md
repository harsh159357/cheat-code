# Reverse Bits

## Problem Statement

Reverse bits of a given 32 bits unsigned integer.

## Input

```text
n = 43261596 (binary: 00000010100101000001111010011100)
```

## Output

```text
964176192 (binary: 00111001011110000010100101000000)
```

## Solutions

### Dart

```dart
int reverseBits(int n) {
  int result = 0;
  for (int i = 0; i < 32; i++) {
    result = (result << 1) | (n & 1);
    n = n >> 1;
  }
  return result;
}
```

### C#

```csharp
public class Solution {
    public uint reverseBits(uint n) {
        uint result = 0;
        for (int i = 0; i < 32; i++) {
            result = (result << 1) | (n & 1);
            n >>= 1;
        }
        return result;
    }
}
```

### Java

```java
public class Solution {
    public int reverseBits(int n) {
        int result = 0;
        for (int i = 0; i < 32; i++) {
            result = (result << 1) | (n & 1);
            n >>= 1;
        }
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun reverseBits(n: Int): Int {
        var result = 0
        var num = n
        repeat(32) {
            result = (result shl 1) or (num and 1)
            num = num shr 1
        }
        return result
    }
}
```

### Swift

```swift
class Solution {
    func reverseBits(_ n: Int) -> Int {
        var result = 0
        var num = n
        for _ in 0..<32 {
            result = (result << 1) | (num & 1)
            num >>= 1
        }
        return result
    }
}
```

### The End

