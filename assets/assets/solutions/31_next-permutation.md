# Next Permutation

## Problem Statement

Implement the **next permutation**, which rearranges numbers into the lexicographically next greater permutation of numbers. If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).

The replacement must be in place and use only constant extra memory.

## Input

```text
nums = [1, 2, 3]
```

## Output

```text
[1, 3, 2]
```

## Solutions

### Dart

```dart
void nextPermutation(List<int> nums) {
  int i = nums.length - 2;

  while (i >= 0 && nums[i] >= nums[i + 1]) {
    i--;
  }

  if (i >= 0) {
    int j = nums.length - 1;
    while (nums[j] <= nums[i]) {
      j--;
    }
    _swap(nums, i, j);
  }

  _reverse(nums, i + 1);
}

void _swap(List<int> nums, int i, int j) {
  int temp = nums[i];
  nums[i] = nums[j];
  nums[j] = temp;
}

void _reverse(List<int> nums, int start) {
  int end = nums.length - 1;
  while (start < end) {
    _swap(nums, start, end);
    start++;
    end--;
  }
}

void main() {
  List<int> nums = [1, 2, 3];
  nextPermutation(nums);
  print(nums); // Output: [1, 3, 2]

  nums = [3, 2, 1];
  nextPermutation(nums);
  print(nums); // Output: [1, 2, 3]

  nums = [1, 1, 5];
  nextPermutation(nums);
  print(nums); // Output: [1, 5, 1]
}
```

### C#

```csharp
public class Solution {
    public void NextPermutation(int[] nums) {
        int i = nums.Length - 2;

        while (i >= 0 && nums[i] >= nums[i + 1]) {
            i--;
        }

        if (i >= 0) {
            int j = nums.Length - 1;
            while (nums[j] <= nums[i]) {
                j--;
            }
            Swap(nums, i, j);
        }

        Reverse(nums, i + 1);
    }

    private void Swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    private void Reverse(int[] nums, int start) {
        int end = nums.Length - 1;
        while (start < end) {
            Swap(nums, start, end);
            start++;
            end--;
        }
    }
}
```

### Java

```java
class Solution {
    public void nextPermutation(int[] nums) {
        int i = nums.length - 2;

        while (i >= 0 && nums[i] >= nums[i + 1]) {
            i--;
        }

        if (i >= 0) {
            int j = nums.length - 1;
            while (nums[j] <= nums[i]) {
                j--;
            }
            swap(nums, i, j);
        }

        reverse(nums, i + 1);
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    private void reverse(int[] nums, int start) {
        int end = nums.length - 1;
        while (start < end) {
            swap(nums, start, end);
            start++;
            end--;
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun nextPermutation(nums: IntArray) {
        var i = nums.size - 2

        while (i >= 0 && nums[i] >= nums[i + 1]) {
            i--
        }

        if (i >= 0) {
            var j = nums.size - 1
            while (nums[j] <= nums[i]) {
                j--
            }
            nums.swap(i, j)
        }

        reverse(nums, i + 1, nums.size - 1)
    }

    private fun IntArray.swap(i: Int, j: Int) {
        val temp = this[i]
        this[i] = this[j]
        this[j] = temp
    }

    private fun reverse(nums: IntArray, start: Int, end: Int) {
        var i = start
        var j = end
        while (i < j) {
            nums.swap(i, j)
            i++
            j--
        }
    }
}
```

### Swift

```swift
class Solution {
    func nextPermutation(_ nums: inout [Int]) {
        var i = nums.count - 2

        while i >= 0 && nums[i] >= nums[i + 1] {
            i -= 1
        }

        if i >= 0 {
            var j = nums.count - 1
            while nums[j] <= nums[i] {
                j -= 1
            }
            nums.swapAt(i, j)
        }

        reverse(&nums, i + 1)
    }

    private func reverse(_ nums: inout [Int], _ start: Int) {
        var i = start
        var j = nums.count - 1
        while i < j {
            nums.swapAt(i, j)
            i += 1
            j -= 1
        }
    }
}

var nums = [1, 2, 3]
Solution().nextPermutation(&nums)
print(nums) // Output: [1, 3, 2]

nums = [3, 2, 1]
Solution().nextPermutation(&nums)
print(nums) // Output: [1, 2, 3]

nums = [1, 1, 5]
Solution().nextPermutation(&nums)
print(nums) // Output: [1, 5, 1]
```


### The End

