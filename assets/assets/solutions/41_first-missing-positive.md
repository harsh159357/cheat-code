# First Missing Positive

## Problem Statement

Given an unsorted integer array `nums`, return the smallest missing positive integer.

You must implement an algorithm that runs in `O(n)` time and uses constant extra space.

## Input

```text
nums = [3, 4, -1, 1]
```

## Output

```text
2  
(Explanation: The smallest missing positive integer is 2.)
```

## Solutions

### Dart

```dart
int firstMissingPositive(List<int> nums) {
  int n = nums.length;
  int i = 0;

  while (i < n) {
    if (nums[i] > 0 && nums[i] <= n && nums[i] != nums[nums[i] - 1]) {
      swap(nums, i, nums[i] - 1);
    } else {
      i++;
    }
  }

  for (int j = 0; j < n; j++) {
    if (nums[j] != j + 1) {
      return j + 1;
    }
  }

  return n + 1;
}

void swap(List<int> nums, int i, int j) {
  int temp = nums[i];
  nums[i] = nums[j];
  nums[j] = temp;
}

void main() {
  print(firstMissingPositive([3, 4, -1, 1])); // Output: 2
  print(firstMissingPositive([1, 2, 0])); // Output: 3
}
```

### C#

```csharp
public class Solution {
    public int FirstMissingPositive(int[] nums) {
        int n = nums.Length;
        int i = 0;

        while (i < n) {
            if (nums[i] > 0 && nums[i] <= n && nums[i] != nums[nums[i] - 1]) {
                Swap(nums, i, nums[i] - 1);
            } else {
                i++;
            }
        }

        for (int j = 0; j < n; j++) {
            if (nums[j] != j + 1) {
                return j + 1;
            }
        }

        return n + 1;
    }

    private void Swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

### Java

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;
        int i = 0;

        while (i < n) {
            if (nums[i] > 0 && nums[i] <= n && nums[i] != nums[nums[i] - 1]) {
                swap(nums, i, nums[i] - 1);
            } else {
                i++;
            }
        }

        for (int j = 0; j < n; j++) {
            if (nums[j] != j + 1) {
                return j + 1;
            }
        }

        return n + 1;
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun firstMissingPositive(nums: IntArray): Int {
        var i = 0
        val n = nums.size

        while (i < n) {
            if (nums[i] in 1..n && nums[i] != nums[nums[i] - 1]) {
                nums.swap(i, nums[i] - 1)
            } else {
                i++
            }
        }

        for (j in 0 until n) {
            if (nums[j] != j + 1) {
                return j + 1
            }
        }

        return n + 1
    }

    private fun IntArray.swap(i: Int, j: Int) {
        val temp = this[i]
        this[i] = this[j]
        this[j] = temp
    }
}
```

### Swift

```swift
class Solution {
    func firstMissingPositive(_ nums: inout [Int]) -> Int {
        let n = nums.count
        var i = 0

        while i < n {
            if nums[i] > 0 && nums[i] <= n && nums[i] != nums[nums[i] - 1] {
                nums.swapAt(i, nums[i] - 1)
            } else {
                i += 1
            }
        }

        for j in 0..<n {
            if nums[j] != j + 1 {
                return j + 1
            }
        }

        return n + 1
    }
}

var nums1 = [3, 4, -1, 1]
var nums2 = [1, 2, 0]

let solution = Solution()
print(solution.firstMissingPositive(&nums1)) // Output: 2
print(solution.firstMissingPositive(&nums2)) // Output: 3
```


### The End

