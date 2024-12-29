# Remove Duplicates from Sorted Array

## Problem Statement

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

Return `k` after placing the final result in the first `k` slots of `nums`.

## Input

```text
nums = [1, 1, 2]
```

## Output

```text
k = 2, nums = [1, 2, _]
```

## Solutions

### Dart

```dart
int removeDuplicates(List<int> nums) {
  if (nums.isEmpty) return 0;

  int k = 1; // Counter for unique elements

  for (int i = 1; i < nums.length; i++) {
    if (nums[i] != nums[i - 1]) {
      nums[k] = nums[i];
      k++;
    }
  }

  return k;
}

void main() {
  List<int> nums1 = [1, 1, 2];
  print("Output 1: ${removeDuplicates(nums1)}, nums = $nums1"); // Output: 2, nums = [1, 2, _]

  List<int> nums2 = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4];
  print("Output 2: ${removeDuplicates(nums2)}, nums = $nums2"); // Output: 5, nums = [0, 1, 2, 3, 4, _]
}
```

### C#

```csharp
public class Solution {
    public int RemoveDuplicates(int[] nums) {
        if (nums.Length == 0) return 0;

        int k = 1; // Counter for unique elements

        for (int i = 1; i < nums.Length; i++) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                k++;
            }
        }

        return k;
    }
}
```

### Java

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;

        int k = 1; // Counter for unique elements

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                k++;
            }
        }

        return k;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun removeDuplicates(nums: IntArray): Int {
        if (nums.isEmpty()) return 0

        var k = 1 // Counter for unique elements

        for (i in 1 until nums.size) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i]
                k++
            }
        }

        return k
    }
}

fun main() {
    val nums1 = intArrayOf(1, 1, 2)
    println("Output 1: ${Solution().removeDuplicates(nums1)}, nums = ${nums1.joinToString()}")

    val nums2 = intArrayOf(0, 0, 1, 1, 1, 2, 2, 3, 3, 4)
    println("Output 2: ${Solution().removeDuplicates(nums2)}, nums = ${nums2.joinToString()}")
}
```

### Swift

```swift
class Solution {
    func removeDuplicates(_ nums: inout [Int]) -> Int {
        if nums.isEmpty { return 0 }

        var k = 1 // Counter for unique elements

        for i in 1..<nums.count {
            if nums[i] != nums[i - 1] {
                nums[k] = nums[i]
                k += 1
            }
        }

        return k
    }
}

var nums1 = [1, 1, 2]
print("Output 1: \(Solution().removeDuplicates(&nums1)), nums = \(nums1)")

var nums2 = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
print("Output 2: \(Solution().removeDuplicates(&nums2)), nums = \(nums2)")
```


### The End

