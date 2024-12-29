# Find Minimum in Rotated Sorted Array II

## Problem Statement

Given a rotated sorted array `nums` that may contain duplicates, find the minimum element of this array.

You must decrease the overall runtime complexity as much as possible.

---

## Input

```text
nums = [2, 2, 2, 0, 1]
```

---

## Output

```text
0
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

            when {
                nums[mid] > nums[right] -> left = mid + 1 // Minimum is in the right half
                nums[mid] < nums[right] -> right = mid    // Minimum is in the left half (or mid itself)
                else -> right-- // We don't know which side the minimum is, so decrement right
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
    } else if (nums[mid] < nums[right]) {
      right = mid;
    } else {
      right--; // Decrement to handle duplicates
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
            } else if (nums[mid] < nums[right]) {
                right = mid;
            } else {
                right--; // Handle duplicates
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
            } else if (nums[mid] < nums[right]) {
                right = mid;
            } else {
                right--; // Handle duplicates
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
            } else if nums[mid] < nums[right] {
                right = mid
            } else {
                right -= 1 // Handle duplicates
            }
        }

        return nums[left]
    }
}
```

### The End

