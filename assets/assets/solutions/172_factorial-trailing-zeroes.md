# Factorial Trailing Zeroes

## Problem Statement

Given an integer `n`, return the number of trailing zeroes in `n!`.

---

## Input

```text
n = 25
```

---

## Output

```text
6
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun trailingZeroes(n: Int): Int {
        var count = 0
        var num = n
        while (num >= 5) {
            count += num / 5
            num /= 5
        }
        return count
    }
}
```


### Dart

```dart
int trailingZeroes(int n) {
  int count = 0;
  int num = n;
  while (num >= 5) {
    count += num ~/ 5;
    num ~/= 5;
  }
  return count;
}
```


### C#

```csharp
public class Solution {
    public int TrailingZeroes(int n) {
        int count = 0;
        while (n >= 5) {
            count += n / 5;
            n /= 5;
        }
        return count;
    }
}
```


### Java

```java
class Solution {
    public int trailingZeroes(int n) {
        int count = 0;
        while (n >= 5) {
            count += n / 5;
            n /= 5;
        }
        return count;
    }
}
```


### Swift

```swift
class Solution {
    func trailingZeroes(_ n: Int) -> Int {
        var count = 0
        var num = n
        while num >= 5 {
            count += num / 5
            num /= 5
        }
        return count
    }
}
```


### The End

