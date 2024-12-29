# Remove Duplicates from Sorted Array II

## Problem Statement

Given an integer array `nums` sorted in **non-decreasing order**, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array `nums`. More formally, if there are `k` elements after removing the duplicates, then the first `k` elements of `nums` should hold the final result. It does not matter what you leave beyond the first `k` elements.

Return `k` after placing the final result in the first `k` slots of `nums`.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with `O(1)` extra memory.

## Input

```text
nums = [1,1,1,2,2,3]
```

## Output

```text
5, nums = [1,1,2,2,3,_]
```

(Explanation: The array after removing duplicates looks like `[1,1,2,2,3]`.)

## Solutions

### Dart

```dart
int removeDuplicates(List<int> nums) {
  int count = 1;
  bool duplicated = false;

  for (int i = 1; i < nums.length; i++) {
    if (nums[i] == nums[i - 1]) {
      if (!duplicated) {
        nums[count] = nums[i];
        count++;
        duplicated = true;
      }
    } else {
      nums[count] = nums[i];
      count++;
      duplicated = false;
    }
  }

  return count;
}

void main() {
  List<int> nums1 = [1, 1, 1, 2, 2, 3];
  List<int> nums2 = [0, 0, 1, 1, 1, 1, 2, 3, 3];
  print(removeDuplicates(nums1)); // Output: 5, nums = [1, 1, 2, 2, 3]
  print(removeDuplicates(nums2)); // Output: 7, nums = [0, 0, 1, 1, 2, 3, 3]
}
```

### C#

```csharp
public class Solution {
    public int RemoveDuplicates(int[] nums) {
        int count = 1;
        bool duplicated = false;

        for (int i = 1; i < nums.Length; i++) {
            if (nums[i] == nums[i - 1]) {
                if (!duplicated) {
                    nums[count] = nums[i];
                    count++;
                    duplicated = true;
                }
            } else {
                nums[count] = nums[i];
                count++;
                duplicated = false;
            }
        }

        return count;
    }
}
```

### Java

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int count = 1;
        boolean duplicated = false;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] == nums[i - 1]) {
                if (!duplicated) {
                    nums[count] = nums[i];
                    count++;
                    duplicated = true;
                }
            } else {
                nums[count] = nums[i];
                count++;
                duplicated = false;
            }
        }

        return count;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun removeDuplicates(nums: IntArray): Int {
        var count = 1
        var duplicated = false

        for (i in 1 until nums.size) {
            if (nums[i] == nums[i - 1]) {
                if (!duplicated) {
                    nums[count] = nums[i]
                    count++
                    duplicated = true
                }
            } else {
                nums[count] = nums[i]
                count++
                duplicated = false
            }
        }

        return count
    }
}

fun main() {
    val nums1 = intArrayOf(1, 1, 1, 2, 2, 3)
    val nums2 = intArrayOf(0, 0, 1, 1, 1, 1, 2, 3, 3)
    println(Solution().removeDuplicates(nums1)) // Output: 5, nums = [1, 1, 2, 2, 3]
    println(Solution().removeDuplicates(nums2)) // Output: 7, nums = [0, 0, 1, 1, 2, 3, 3]
}
```

### Swift

```swift
class Solution {
    func removeDuplicates(_ nums: inout [Int]) -> Int {
        var count = 1
        var duplicated = false

        for i in 1..<nums.count {
            if nums[i] == nums[i - 1] {
                if !duplicated {
                    nums[count] = nums[i]
                    count += 1
                    duplicated = true
                }
            } else {
                nums[count] = nums[i]
                count += 1
                duplicated = false
            }
        }

        return count
    }
}

var nums1 = [1, 1, 1, 2, 2, 3]
var nums2 = [0, 0, 1, 1, 1, 1, 2, 3, 3]
print(Solution().removeDuplicates(&nums1)) // Output: 5, nums = [1, 1, 2, 2, 3]
print(Solution().removeDuplicates(&nums2)) // Output: 7, nums = [0, 0, 1, 1, 2, 3, 3]
```

### The End

