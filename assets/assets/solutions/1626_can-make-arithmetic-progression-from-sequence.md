# Can Make Arithmetic Progression From Sequence

## Problem Statement

Given an array of numbers `arr`, return `true` if the array can be rearranged to form an arithmetic progression, otherwise return `false`.

An **arithmetic progression** is a sequence of numbers such that the difference between any two consecutive terms is the same.

## Input

```text
arr = [3, 5, 1]
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun canMakeArithmeticProgression(arr: IntArray): Boolean {
        arr.sort()
        val diff = arr[1] - arr[0]
        for (i in 2 until arr.size) {
            if (arr[i] - arr[i - 1] != diff) {
                return false
            }
        }
        return true
    }
}
```

### Dart

```dart
bool canMakeArithmeticProgression(List<int> arr) {
  arr.sort();
  int diff = arr[1] - arr[0];
  for (int i = 2; i < arr.length; i++) {
    if (arr[i] - arr[i - 1] != diff) {
      return false;
    }
  }
  return true;
}
```

### C#

```csharp
public class Solution {
    public bool CanMakeArithmeticProgression(int[] arr) {
        Array.Sort(arr);
        int diff = arr[1] - arr[0];
        for (int i = 2; i < arr.Length; i++) {
            if (arr[i] - arr[i - 1] != diff) {
                return false;
            }
        }
        return true;
    }
}
```

### Java

```java
class Solution {
    public boolean canMakeArithmeticProgression(int[] arr) {
        Arrays.sort(arr);
        int diff = arr[1] - arr[0];
        for (int i = 2; i < arr.length; i++) {
            if (arr[i] - arr[i - 1] != diff) {
                return false;
            }
        }
        return true;
    }
}
```

### Swift

```swift
class Solution {
    func canMakeArithmeticProgression(_ arr: [Int]) -> Bool {
        let sortedArr = arr.sorted()
        let diff = sortedArr[1] - sortedArr[0]
        for i in 2..<sortedArr.count {
            if sortedArr[i] - sortedArr[i - 1] != diff {
                return false
            }
        }
        return true
    }
}
```

### The End