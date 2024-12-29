# H-Index II

## Problem Statement

Given an array of integers `citations` sorted in ascending order, where `citations[i]` is the number of citations a researcher received for their `i-th` paper, compute the researcher's h-index.

The h-index is defined as the maximum value of `h` such that the researcher has published at least `h` papers that have each been cited at least `h` times.

## Input

```text
citations = [0, 1, 3, 5, 6]
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int hIndex(List<int> citations) {
  int n = citations.length;
  int left = 0, right = n - 1;

  while (left <= right) {
    int mid = left + (right - left) ~/ 2;
    if (citations[mid] == n - mid) {
      return n - mid;
    } else if (citations[mid] < n - mid) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }

  return n - left;
}
```

### C#

```csharp
public class Solution {
    public int HIndex(int[] citations) {
        int n = citations.Length;
        int left = 0, right = n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (citations[mid] == n - mid) {
                return n - mid;
            } else if (citations[mid] < n - mid) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return n - left;
    }
}
```

### Java

```java
class Solution {
    public int hIndex(int[] citations) {
        int n = citations.length;
        int left = 0, right = n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (citations[mid] == n - mid) {
                return n - mid;
            } else if (citations[mid] < n - mid) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return n - left;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun hIndex(citations: IntArray): Int {
        val n = citations.size
        var left = 0
        var right = n - 1
        while (left <= right) {
            val mid = left + (right - left) / 2
            if (citations[mid] == n - mid) {
                return n - mid
            } else if (citations[mid] < n - mid) {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }
        return n - left
    }
}
```

### Swift

```swift
class Solution {
    func hIndex(_ citations: [Int]) -> Int {
        let n = citations.count
        var left = 0, right = n - 1

        while left <= right {
            let mid = left + (right - left) / 2
            if citations[mid] == n - mid {
                return n - mid
            } else if citations[mid] < n - mid {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return n - left
    }
}
```

### The End

