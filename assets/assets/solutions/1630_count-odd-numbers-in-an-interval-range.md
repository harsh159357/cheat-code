# Count Odd Numbers in an Interval Range

## Problem Statement

Given two non-negative integers `low` and `high`, return the count of odd numbers between `low` and `high` (inclusive).

## Input

```text
low = 3, high = 7
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun countOdds(low: Int, high: Int): Int {
        return if (low % 2 == 0 && high % 2 == 0) {
            (high - low) / 2
        } else {
            (high - low) / 2 + 1
        }
    }
}
```

### Dart

```dart
int countOdds(int low, int high) {
  return (low % 2 == 0 && high % 2 == 0) 
      ? (high - low) ~/ 2 
      : (high - low) ~/ 2 + 1;
}
```

### C#

```csharp
public class Solution {
    public int CountOdds(int low, int high) {
        if (low % 2 == 0 && high % 2 == 0) {
            return (high - low) / 2;
        } else {
            return (high - low) / 2 + 1;
        }
    }
}
```

### Java

```java
class Solution {
    public int countOdds(int low, int high) {
        if (low % 2 == 0 && high % 2 == 0) {
            return (high - low) / 2;
        } else {
            return (high - low) / 2 + 1;
        }
    }
}
```

### Swift

```swift
class Solution {
    func countOdds(_ low: Int, _ high: Int) -> Int {
        if low % 2 == 0 && high % 2 == 0 {
            return (high - low) / 2
        } else {
            return (high - low) / 2 + 1
        }
    }
}
```

### The End