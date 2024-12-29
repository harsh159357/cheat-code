# Kth Missing Positive Number

## Problem Statement

Given an array `arr` of positive integers sorted in a strictly increasing order, and an integer `k`, return the `k`-th positive integer that is missing from this array.

## Input

```text
arr = [2, 3, 4, 7, 11], k = 5
```

## Output

```text
9
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun findKthPositive(arr: IntArray, k: Int): Int {
        var left = 0
        var right = arr.size
        while (left < right) {
            val mid = left + (right - left) / 2
            if (arr[mid] - mid - 1 < k) {
                left = mid + 1
            } else {
                right = mid
            }
        }
        return left + k
    }
}

fun main() {
    val arr = intArrayOf(2, 3, 4, 7, 11)
    val k = 5
    println(Solution().findKthPositive(arr, k)) // Output: 9
}
```

### Dart

```dart
int findKthPositive(List<int> arr, int k) {
  int left = 0, right = arr.length;

  while (left < right) {
    int mid = left + (right - left) ~/ 2;
    if (arr[mid] - mid - 1 < k) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }

  return left + k;
}

void main() {
  List<int> arr = [2, 3, 4, 7, 11];
  int k = 5;
  print(findKthPositive(arr, k)); // Output: 9
}
```

### C#

```csharp
public class Solution {
    public int FindKthPositive(int[] arr, int k) {
        int left = 0, right = arr.Length;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] - mid - 1 < k) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return left + k;
    }
}
```

### Java

```java
class Solution {
    public int findKthPositive(int[] arr, int k) {
        int left = 0, right = arr.length;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] - mid - 1 < k) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return left + k;
    }
}
```

### Swift

```swift
class Solution {
    func findKthPositive(_ arr: [Int], _ k: Int) -> Int {
        var left = 0
        var right = arr.count

        while left < right {
            let mid = left + (right - left) / 2
            if arr[mid] - mid - 1 < k {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return left + k
    }
}
```

### The End