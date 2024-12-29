# Peak Index in a Mountain Array

## Problem Statement

Given a mountain array `arr`, return the index of the peak element. A mountain array is defined as an array where:

1. `arr.length >= 3`
2. There exists some `i` with `0 < i < arr.length - 1` such that:
    - `arr[0] < arr[1] < ... < arr[i]`
    - `arr[i] > arr[i+1] > ... > arr[arr.length - 1]`

You need to find the peak index `i`.

## Input

```text
arr = [0, 1, 0]
```

## Output

```text
1
```

## Solutions

### Dart

```dart
int peakIndexInMountainArray(List<int> arr) {
  int left = 0, right = arr.length - 1;

  while (left < right) {
    int mid = left + (right - left) ~/ 2;
    if (arr[mid] < arr[mid + 1]) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }

  return left;
}
```

### C#

```csharp
public class Solution {
    public int PeakIndexInMountainArray(int[] arr) {
        int left = 0, right = arr.Length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] < arr[mid + 1]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return left;
    }
}
```

### Java

```java
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        int left = 0, right = arr.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] < arr[mid + 1]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return left;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun peakIndexInMountainArray(arr: IntArray): Int {
        var left = 0
        var right = arr.size - 1

        while (left < right) {
            val mid = left + (right - left) / 2
            if (arr[mid] < arr[mid + 1]) {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return left
    }
}
```

### Swift

```swift
class Solution {
    func peakIndexInMountainArray(_ arr: [Int]) -> Int {
        var left = 0, right = arr.count - 1

        while left < right {
            let mid = left + (right - left) / 2
            if arr[mid] < arr[mid + 1] {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return left
    }
}
```


### The End