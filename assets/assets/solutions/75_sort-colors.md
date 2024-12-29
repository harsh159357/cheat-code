# Sort Colors

## Problem Statement

Given an array `nums` with `n` objects colored red, white, or blue, sort them **in-place** so that objects of the same color are adjacent, with the colors in the order red, white, and blue. We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.

## Input

```text
nums = [2, 0, 2, 1, 1, 0]
```

## Output

```text
[0, 0, 1, 1, 2, 2]
```

## Solutions

### Dart

```dart
void sortColors(List<int> nums) {
  int low = 0;
  int high = nums.length - 1;
  int current = 0;

  while (current <= high) {
    if (nums[current] == 0) {
      int temp = nums[current];
      nums[current] = nums[low];
      nums[low] = temp;
      low++;
      current++;
    } else if (nums[current] == 2) {
      int temp = nums[current];
      nums[current] = nums[high];
      nums[high] = temp;
      high--;
    } else {
      current++;
    }
  }
}

void main() {
  var nums = [2, 0, 2, 1, 1, 0];
  sortColors(nums);
  print(nums); // Output: [0, 0, 1, 1, 2, 2]
}
```

### C#

```csharp
public class Solution {
    public void SortColors(int[] nums) {
        int low = 0, high = nums.Length - 1, current = 0;

        while (current <= high) {
            if (nums[current] == 0) {
                int temp = nums[current];
                nums[current] = nums[low];
                nums[low] = temp;
                low++;
                current++;
            } else if (nums[current] == 2) {
                int temp = nums[current];
                nums[current] = nums[high];
                nums[high] = temp;
                high--;
            } else {
                current++;
            }
        }
    }
}
```

### Java

```java
class Solution {
    public void sortColors(int[] nums) {
        int low = 0, high = nums.length - 1, current = 0;

        while (current <= high) {
            if (nums[current] == 0) {
                int temp = nums[current];
                nums[current] = nums[low];
                nums[low] = temp;
                low++;
                current++;
            } else if (nums[current] == 2) {
                int temp = nums[current];
                nums[current] = nums[high];
                nums[high] = temp;
                high--;
            } else {
                current++;
            }
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun sortColors(nums: IntArray) {
        var low = 0
        var high = nums.size - 1
        var current = 0

        while (current <= high) {
            when {
                nums[current] == 0 -> {
                    nums.swap(current, low)
                    low++
                    current++
                }
                nums[current] == 2 -> {
                    nums.swap(current, high)
                    high--
                }
                else -> {
                    current++
                }
            }
        }
    }

    private fun IntArray.swap(i: Int, j: Int) {
        val temp = this[i]
        this[i] = this[j]
        this[j] = temp
    }
}

fun main() {
    val nums = intArrayOf(2, 0, 2, 1, 1, 0)
    Solution().sortColors(nums)
    println(nums.toList()) // Output: [0, 0, 1, 1, 2, 2]
}
```

### Swift

```swift
class Solution {
    func sortColors(_ nums: inout [Int]) {
        var low = 0
        var high = nums.count - 1
        var current = 0

        while current <= high {
            if nums[current] == 0 {
                nums.swapAt(current, low)
                low += 1
                current += 1
            } else if nums[current] == 2 {
                nums.swapAt(current, high)
                high -= 1
            } else {
                current += 1
            }
        }
    }
}

var nums = [2, 0, 2, 1, 1, 0]
Solution().sortColors(&nums)
print(nums) // Output: [0, 0, 1, 1, 2, 2]
```

### The End

