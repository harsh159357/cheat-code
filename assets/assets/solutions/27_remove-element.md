# Remove Element

## Problem Statement

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in-place. The relative order of the elements may be changed.

Return `k` after placing the final result in the first `k` slots of `nums`.

## Input

```text
nums = [3, 2, 2, 3], val = 3
```

## Output

```text
k = 2, nums = [2, 2, _, _]
```

## Solutions

### Dart

```dart
int removeElement(List<int> nums, int val) {
  int k = 0; // Counter for non-equal elements

  for (int i = 0; i < nums.length; i++) {
    if (nums[i] != val) {
      nums[k] = nums[i];
      k++;
    }
  }

  return k;
}

void main() {
  List<int> nums1 = [3, 2, 2, 3];
  print("Output 1: ${removeElement(nums1, 3)}, nums = $nums1"); // Output: 2, nums = [2, 2, _, _]

  List<int> nums2 = [0, 1, 2, 2, 3, 0, 4, 2];
  print("Output 2: ${removeElement(nums2, 2)}, nums = $nums2"); // Output: 5, nums = [0, 1, 3, 0, 4, _, _, _]
}
```

### C#

```csharp
public class Solution {
    public int RemoveElement(int[] nums, int val) {
        int k = 0; // Counter for non-equal elements

        for (int i = 0; i < nums.Length; i++) {
            if (nums[i] != val) {
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
    public int removeElement(int[] nums, int val) {
        int k = 0; // Counter for non-equal elements

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
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
    fun removeElement(nums: IntArray, `val`: Int): Int {
        var k = 0 // Counter for non-equal elements

        for (i in nums.indices) {
            if (nums[i] != `val`) {
                nums[k] = nums[i]
                k++
            }
        }

        return k
    }
}

fun main() {
    val nums1 = intArrayOf(3, 2, 2, 3)
    println("Output 1: ${Solution().removeElement(nums1, 3)}, nums = ${nums1.joinToString()}")

    val nums2 = intArrayOf(0, 1, 2, 2, 3, 0, 4, 2)
    println("Output 2: ${Solution().removeElement(nums2, 2)}, nums = ${nums2.joinToString()}")
}
```

### Swift

```swift
class Solution {
    func removeElement(_ nums: inout [Int], _ val: Int) -> Int {
        var k = 0 // Counter for non-equal elements

        for i in 0..<nums.count {
            if nums[i] != val {
                nums[k] = nums[i]
                k += 1
            }
        }

        return k
    }
}

var nums1 = [3, 2, 2, 3]
print("Output 1: \(Solution().removeElement(&nums1, 3)), nums = \(nums1)")

var nums2 = [0, 1, 2, 2, 3, 0, 4, 2]
print("Output 2: \(Solution().removeElement(&nums2, 2)), nums = \(nums2)")
```


### The End

