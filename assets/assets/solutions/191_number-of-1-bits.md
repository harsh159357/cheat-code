# Number of 1 Bits

## Problem Statement

Write a function that takes an unsigned integer and returns the number of `1` bits it has (also known as the Hamming weight).

## Input

```text
n = 11 (binary: 00000000000000000000000000001011)
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int hammingWeight(int n) {
  int count = 0;
  while (n != 0) {
    count += n & 1;
    n = n >>> 1; // Unsigned right shift
  }
  return count;
}
```

### C#

```csharp
public class Solution {
    public int HammingWeight(uint n) {
        int count = 0;
        while (n != 0) {
            count += (int)(n & 1);
            n >>= 1;
        }
        return count;
    }
}
```

### Java

```java
public class Solution {
    public int hammingWeight(int n) {
        int count = 0;
        while (n != 0) {
            count += n & 1;
            n >>>= 1;
        }
        return count;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun hammingWeight(n: Int): Int {
        var count = 0
        var num = n
        while (num != 0) {
            count += num and 1
            num = num ushr 1
        }
        return count
    }
}
```

### Swift

```swift
class Solution {
    func hammingWeight(_ n: Int) -> Int {
        var count = 0
        var num = n
        while num != 0 {
            count += num & 1
            num >>= 1
        }
        return count
    }
}
```


### The End

