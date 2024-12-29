# Find Minimum in Rotated Sorted Array

## Problem Statement

Suppose an array of length `n` sorted in ascending order is rotated between `1` and `n` times. You are given a rotated array `nums` of unique elements. Return the minimum element of this array.

You must write an algorithm that runs in `O(log n)` time.

---

## Input

```text
nums = [3, 4, 5, 1, 2]
```

---

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findMin(nums: IntArray): Int {
        var left = 0
        var right = nums.size - 1

        while (left < right) {
            val mid = left + (right - left) / 2
            if (nums[mid] > nums[right]) {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return nums[left]
    }
}
```


### Dart

```dart
int findMin(List<int> nums) {
  int left = 0;
  int right = nums.length - 1;

  while (left < right) {
    int mid = left + (right - left) ~/ 2;
    if (nums[mid] > nums[right]) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }

  return nums[left];
}
```


### C#

```csharp
public class Solution {
    public int FindMin(int[] nums) {
        int left = 0, right = nums.Length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return nums[left];
    }
}
```

### Java

```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0, right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return nums[left];
    }
}
```


### Swift

```swift
class Solution {
    func findMin(_ nums: [Int]) -> Int {
        var left = 0
        var right = nums.count - 1

        while left < right {
            let mid = left + (right - left) / 2
            if nums[mid] > nums[right] {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return nums[left]
    }
}
```



### The End

