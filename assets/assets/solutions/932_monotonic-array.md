# Monotonic Array

## Problem Statement

An array is monotonic if it is either entirely non-increasing or non-decreasing.

Return `true` if and only if the given array `A` is monotonic.

## Input

```text
A = [1, 2, 2, 3]
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun isMonotonic(A: IntArray): Boolean {
        var increasing = true
        var decreasing = true

        for (i in 0 until A.size - 1) {
            if (A[i] > A[i + 1]) increasing = false
            if (A[i] < A[i + 1]) decreasing = false
        }

        return increasing || decreasing
    }
}
```

### Dart

```dart
bool isMonotonic(List<int> A) {
  bool increasing = true;
  bool decreasing = true;

  for (int i = 0; i < A.length - 1; i++) {
    if (A[i] > A[i + 1]) increasing = false;
    if (A[i] < A[i + 1]) decreasing = false;
  }

  return increasing || decreasing;
}
```

### C#

```csharp
public class Solution {
    public bool IsMonotonic(int[] A) {
        bool increasing = true;
        bool decreasing = true;

        for (int i = 0; i < A.Length - 1; i++) {
            if (A[i] > A[i + 1]) increasing = false;
            if (A[i] < A[i + 1]) decreasing = false;
        }

        return increasing || decreasing;
    }
}
```

### Java

```java
class Solution {
    public boolean isMonotonic(int[] A) {
        boolean increasing = true;
        boolean decreasing = true;

        for (int i = 0; i < A.length - 1; i++) {
            if (A[i] > A[i + 1]) increasing = false;
            if (A[i] < A[i + 1]) decreasing = false;
        }

        return increasing || decreasing;
    }
}
```

### Swift

```swift
class Solution {
    func isMonotonic(_ A: [Int]) -> Bool {
        var increasing = true
        var decreasing = true

        for i in 0..<A.count - 1 {
            if A[i] > A[i + 1] { increasing = false }
            if A[i] < A[i + 1] { decreasing = false }
        }

        return increasing || decreasing
    }
}
```

### The End