# Single Element in a Sorted Array

## Problem Statement

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once. Find this single element that appears only once.

You must implement a solution with \(O(\log n)\) runtime complexity.

## Input

```text
nums = [1, 1, 2, 3, 3, 4, 4, 8, 8]
```

## Output

```text
2
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun singleNonDuplicate(nums: IntArray): Int {
        var left = 0
        var right = nums.size - 1

        while (left < right) {
            val mid = left + (right - left) / 2

            // Adjust mid to be even for easier comparison
            if (mid % 2 == 1) mid--

            if (nums[mid] == nums[mid + 1]) {
                left = mid + 2
            } else {
                right = mid
            }
        }

        return nums[left]
    }
}

fun main() {
    val solution = Solution()

    val nums1 = intArrayOf(1, 1, 2, 3, 3, 4, 4, 8, 8)
    println("Single element: ${solution.singleNonDuplicate(nums1)}") // Output: 2

    val nums2 = intArrayOf(3, 3, 7, 7, 10, 11, 11)
    println("Single element: ${solution.singleNonDuplicate(nums2)}") // Output: 10
}
```

---

### Dart

```dart
int singleNonDuplicate(List<int> nums) {
  int left = 0;
  int right = nums.length - 1;

  while (left < right) {
    int mid = left + (right - left) ~/ 2;

    // Adjust mid to be even for easier comparison
    if (mid % 2 == 1) mid--;

    if (nums[mid] == nums[mid + 1]) {
      left = mid + 2;
    } else {
      right = mid;
    }
  }

  return nums[left];
}

void main() {
  print(singleNonDuplicate([1, 1, 2, 3, 3, 4, 4, 8, 8])); // Output: 2
  print(singleNonDuplicate([3, 3, 7, 7, 10, 11, 11]));    // Output: 10
}
```

---

### C#

```csharp
public class Solution {
    public int SingleNonDuplicate(int[] nums) {
        int left = 0, right = nums.Length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            // Adjust mid to be even for easier comparison
            if (mid % 2 == 1) mid--;

            if (nums[mid] == nums[mid + 1]) {
                left = mid + 2;
            } else {
                right = mid;
            }
        }

        return nums[left];
    }
}
```

---

### Java

```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int left = 0, right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            // Adjust mid to be even for easier comparison
            if (mid % 2 == 1) mid--;

            if (nums[mid] == nums[mid + 1]) {
                left = mid + 2;
            } else {
                right = mid;
            }
        }

        return nums[left];
    }
}
```

---

### Swift

```swift
class Solution {
    func singleNonDuplicate(_ nums: [Int]) -> Int {
        var left = 0
        var right = nums.count - 1

        while left < right {
            var mid = left + (right - left) / 2

            // Adjust mid to be even for easier comparison
            if mid % 2 == 1 { mid -= 1 }

            if nums[mid] == nums[mid + 1] {
                left = mid + 2
            } else {
                right = mid
            }
        }

        return nums[left]
    }
}

// Example usage
let solution = Solution()
print(solution.singleNonDuplicate([1, 1, 2, 3, 3, 4, 4, 8, 8])) // Output: 2
print(solution.singleNonDuplicate([3, 3, 7, 7, 10, 11, 11]))    // Output: 10
```

### The End