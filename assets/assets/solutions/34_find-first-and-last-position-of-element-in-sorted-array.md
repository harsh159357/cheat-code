# Find First and Last Position of Element in Sorted Array

## Problem Statement

Given an array of integers `nums` sorted in non-decreasing order, find the starting and ending position of a given target value. If the target is not found in the array, return `[-1, -1]`.

You must write an algorithm with `O(log n)` runtime complexity.

## Input

```text
nums = [5,7,7,8,8,10], target = 8
```

## Output

```text
[3, 4]  
(Explanation: The target value `8` appears at indices 3 and 4.)
```

## Solutions

### Dart

```dart
List<int> searchRange(List<int> nums, int target) {
  int findFirst() {
    int left = 0;
    int right = nums.length - 1;
    int index = -1;

    while (left <= right) {
      int mid = left + (right - left) ~/ 2;
      if (nums[mid] >= target) {
        if (nums[mid] == target) index = mid;
        right = mid - 1;
      } else {
        left = mid + 1;
      }
    }
    return index;
  }

  int findLast() {
    int left = 0;
    int right = nums.length - 1;
    int index = -1;

    while (left <= right) {
      int mid = left + (right - left) ~/ 2;
      if (nums[mid] <= target) {
        if (nums[mid] == target) index = mid;
        left = mid + 1;
      } else {
        right = mid - 1;
      }
    }
    return index;
  }

  int first = findFirst();
  if (first == -1) return [-1, -1];
  return [first, findLast()];
}

void main() {
  print(searchRange([5,7,7,8,8,10], 8)); // Output: [3, 4]
  print(searchRange([5,7,7,8,8,10], 6)); // Output: [-1, -1]
}
```

### C#

```csharp
public class Solution {
    public int[] SearchRange(int[] nums, int target) {
        int FindFirst() {
            int left = 0, right = nums.Length - 1, index = -1;
            while (left <= right) {
                int mid = left + (right - left) / 2;
                if (nums[mid] >= target) {
                    if (nums[mid] == target) index = mid;
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }
            return index;
        }

        int FindLast() {
            int left = 0, right = nums.Length - 1, index = -1;
            while (left <= right) {
                int mid = left + (right - left) / 2;
                if (nums[mid] <= target) {
                    if (nums[mid] == target) index = mid;
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
            return index;
        }

        int first = FindFirst();
        if (first == -1) return new[] { -1, -1 };
        return new[] { first, FindLast() };
    }
}
```

### Java

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int findFirst() {
            int left = 0, right = nums.length - 1, index = -1;
            while (left <= right) {
                int mid = left + (right - left) / 2;
                if (nums[mid] >= target) {
                    if (nums[mid] == target) index = mid;
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }
            return index;
        }

        int findLast() {
            int left = 0, right = nums.length - 1, index = -1;
            while (left <= right) {
                int mid = left + (right - left) / 2;
                if (nums[mid] <= target) {
                    if (nums[mid] == target) index = mid;
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
            return index;
        }

        int first = findFirst();
        if (first == -1) return new int[] { -1, -1 };
        return new int[] { first, findLast() };
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun searchRange(nums: IntArray, target: Int): IntArray {
        fun findFirst(): Int {
            var left = 0
            var right = nums.size - 1
            var index = -1
            while (left <= right) {
                val mid = left + (right - left) / 2
                if (nums[mid] >= target) {
                    if (nums[mid] == target) index = mid
                    right = mid - 1
                } else {
                    left = mid + 1
                }
            }
            return index
        }

        fun findLast(): Int {
            var left = 0
            var right = nums.size - 1
            var index = -1
            while (left <= right) {
                val mid = left + (right - left) / 2
                if (nums[mid] <= target) {
                    if (nums[mid] == target) index = mid
                    left = mid + 1
                } else {
                    right = mid - 1
                }
            }
            return index
        }

        val first = findFirst()
        if (first == -1) return intArrayOf(-1, -1)
        return intArrayOf(first, findLast())
    }
}
```

### Swift

```swift
class Solution {
    func searchRange(_ nums: [Int], _ target: Int) -> [Int] {
        func findFirst() -> Int {
            var left = 0, right = nums.count - 1, index = -1
            while left <= right {
                let mid = left + (right - left) / 2
                if nums[mid] >= target {
                    if nums[mid] == target { index = mid }
                    right = mid - 1
                } else {
                    left = mid + 1
                }
            }
            return index
        }

        func findLast() -> Int {
            var left = 0, right = nums.count - 1, index = -1
            while left <= right {
                let mid = left + (right - left) / 2
                if nums[mid] <= target {
                    if nums[mid] == target { index = mid }
                    left = mid + 1
                } else {
                    right = mid - 1
                }
            }
            return index
        }

        let first = findFirst()
        if first == -1 { return [-1, -1] }
        return [first, findLast()]
    }
}

let solution = Solution()
print(solution.searchRange([5,7,7,8,8,10], 8)) // Output: [3, 4]
print(solution.searchRange([5,7,7,8,8,10], 6)) // Output: [-1, -1]
```


### The End

