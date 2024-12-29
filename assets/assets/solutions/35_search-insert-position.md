# Search Insert Position

## Problem Statement

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

## Input

```text
nums = [1,3,5,6], target = 5
```

## Output

```text
2  
(Explanation: The target value `5` is found at index 2.)
```

## Solutions

### Dart

```dart
int searchInsert(List<int> nums, int target) {
  int left = 0;
  int right = nums.length - 1;

  while (left <= right) {
    int mid = left + (right - left) ~/ 2;

    if (nums[mid] == target) return mid;

    if (nums[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }

  return left;
}

void main() {
  print(searchInsert([1, 3, 5, 6], 5)); // Output: 2
  print(searchInsert([1, 3, 5, 6], 2)); // Output: 1
  print(searchInsert([1, 3, 5, 6], 7)); // Output: 4
}
```

### C#

```csharp
public class Solution {
    public int SearchInsert(int[] nums, int target) {
        int left = 0, right = nums.Length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) return mid;

            if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return left;
    }
}
```

### Java

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) return mid;

            if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return left;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun searchInsert(nums: IntArray, target: Int): Int {
        var left = 0
        var right = nums.size - 1

        while (left <= right) {
            val mid = left + (right - left) / 2

            if (nums[mid] == target) return mid

            if (nums[mid] < target) {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return left
    }
}
```

### Swift

```swift
class Solution {
    func searchInsert(_ nums: [Int], _ target: Int) -> Int {
        var left = 0
        var right = nums.count - 1

        while left <= right {
            let mid = left + (right - left) / 2

            if nums[mid] == target {
                return mid
            }

            if nums[mid] < target {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return left
    }
}

let solution = Solution()
print(solution.searchInsert([1, 3, 5, 6], 5)) // Output: 2
print(solution.searchInsert([1, 3, 5, 6], 2)) // Output: 1
print(solution.searchInsert([1, 3, 5, 6], 7)) // Output: 4
```


### The End

