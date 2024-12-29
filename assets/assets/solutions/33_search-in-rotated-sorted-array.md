# Search in Rotated Sorted Array

## Problem Statement

There is an integer array `nums` sorted in ascending order (with distinct values). Prior to being passed to your function, `nums` is possibly rotated at an unknown pivot index. For example, `[0,1,2,4,5,6,7]` might become `[4,5,6,7,0,1,2]`.

Given the array `nums` after the possible rotation and an integer `target`, return the index of `target` if it is in `nums`, or `-1` if it is not in `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

## Input

```text
nums = [4,5,6,7,0,1,2], target = 0
```

## Output

```text
4  
(Explanation: The index of `target` 0 in the rotated array is 4.)
```

## Solutions

### Dart

```dart
int search(List<int> nums, int target) {
  int left = 0;
  int right = nums.length - 1;

  while (left <= right) {
    int mid = left + (right - left) ~/ 2;

    if (nums[mid] == target) return mid;

    if (nums[left] <= nums[mid]) {
      if (nums[left] <= target && target < nums[mid]) {
        right = mid - 1;
      } else {
        left = mid + 1;
      }
    } else {
      if (nums[mid] < target && target <= nums[right]) {
        left = mid + 1;
      } else {
        right = mid - 1;
      }
    }
  }

  return -1;
}

void main() {
  print(search([4, 5, 6, 7, 0, 1, 2], 0)); // Output: 4
  print(search([4, 5, 6, 7, 0, 1, 2], 3)); // Output: -1
}
```

### C#

```csharp
public class Solution {
    public int Search(int[] nums, int target) {
        int left = 0, right = nums.Length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) return mid;

            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else {
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }

        return -1;
    }
}
```

### Java

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) return mid;

            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else {
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }

        return -1;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun search(nums: IntArray, target: Int): Int {
        var left = 0
        var right = nums.size - 1

        while (left <= right) {
            val mid = left + (right - left) / 2

            if (nums[mid] == target) return mid

            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1
                } else {
                    left = mid + 1
                }
            } else {
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1
                } else {
                    right = mid - 1
                }
            }
        }

        return -1
    }
}
```

### Swift

```swift
class Solution {
    func search(_ nums: [Int], _ target: Int) -> Int {
        var left = 0
        var right = nums.count - 1

        while left <= right {
            let mid = left + (right - left) / 2

            if nums[mid] == target {
                return mid
            }

            if nums[left] <= nums[mid] {
                if nums[left] <= target && target < nums[mid] {
                    right = mid - 1
                } else {
                    left = mid + 1
                }
            } else {
                if nums[mid] < target && target <= nums[right] {
                    left = mid + 1
                } else {
                    right = mid - 1
                }
            }
        }

        return -1
    }
}

let solution = Solution()
print(solution.search([4, 5, 6, 7, 0, 1, 2], 0)) // Output: 4
print(solution.search([4, 5, 6, 7, 0, 1, 2], 3)) // Output: -1
```


### The End

