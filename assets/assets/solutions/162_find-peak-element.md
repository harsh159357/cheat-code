# Find Peak Element

## Problem Statement

A peak element is an element that is strictly greater than its neighbors. Given an integer array `nums`, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that `nums[-1] = nums[n] = -∞`.

You must write an algorithm that runs in `O(log n)` time.

---

## Input

```text
nums = [1, 2, 3, 1]
```

---

## Output

```text
2
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun findPeakElement(nums: IntArray): Int {
        var left = 0
        var right = nums.size - 1
        while (left < right) {
            val mid = left + (right - left) / 2
            if (nums[mid] < nums[mid + 1]) {
                left = mid + 1
            } else {
                right = mid
            }
        }
        return left
    }
}
```


### Dart

```dart
int findPeakElement(List<int> nums) {
  int left = 0, right = nums.length - 1;
  while (left < right) {
    int mid = left + (right - left) ~/ 2;
    if (nums[mid] < nums[mid + 1]) {
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
    public int FindPeakElement(int[] nums) {
        int left = 0, right = nums.Length - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < nums[mid + 1]) {
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
    public int findPeakElement(int[] nums) {
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < nums[mid + 1]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return left;
    }
}
```


### Swift

```swift
class Solution {
    func findPeakElement(_ nums: [Int]) -> Int {
        var left = 0
        var right = nums.count - 1
        while left < right {
            let mid = left + (right - left) / 2
            if nums[mid] < nums[mid + 1] {
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

