# Valid Triangle Number

## Problem Statement

Given an integer array `nums`, return the number of triplets chosen from the array that can make triangles if we take them as side lengths of a triangle.

## Constraints

- A valid triangle satisfies the triangle inequality: the sum of any two sides must be greater than the third side.

## Input

```text
nums = [2, 2, 3, 4]
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun triangleNumber(nums: IntArray): Int {
        if (nums.size < 3) return 0

        nums.sort()

        var triangles = 0
        for (i in nums.size - 1 downTo 2) {
            val largestSide = nums[i]
            var left = 0
            var right = i - 1

            while (left < right) {
                if (nums[left] + nums[right] > largestSide) {
                    triangles += right - left
                    right--
                } else {
                    left++
                }
            }
        }

        return triangles
    }
}

fun main() {
    val nums = intArrayOf(2, 2, 3, 4)
    val solution = Solution()
    println("Number of valid triangles: ${solution.triangleNumber(nums)}") // Output: 3
}
```

### Dart

```dart
int triangleNumber(List<int> nums) {
  if (nums.length < 3) return 0;

  nums.sort();
  int triangles = 0;

  for (int i = nums.length - 1; i >= 2; i--) {
    int largestSide = nums[i];
    int left = 0, right = i - 1;

    while (left < right) {
      if (nums[left] + nums[right] > largestSide) {
        triangles += right - left;
        right--;
      } else {
        left++;
      }
    }
  }

  return triangles;
}

void main() {
  List<int> nums = [2, 2, 3, 4];
  print("Number of valid triangles: ${triangleNumber(nums)}"); // Output: 3
}
```

### C#

```csharp
public class Solution {
    public int TriangleNumber(int[] nums) {
        if (nums.Length < 3) return 0;

        Array.Sort(nums);
        int triangles = 0;

        for (int i = nums.Length - 1; i >= 2; i--) {
            int left = 0, right = i - 1;

            while (left < right) {
                if (nums[left] + nums[right] > nums[i]) {
                    triangles += right - left;
                    right--;
                } else {
                    left++;
                }
            }
        }

        return triangles;
    }
}
```

### Java

```java
import java.util.Arrays;

class Solution {
    public int triangleNumber(int[] nums) {
        if (nums.length < 3) return 0;

        Arrays.sort(nums);
        int triangles = 0;

        for (int i = nums.length - 1; i >= 2; i--) {
            int left = 0, right = i - 1;

            while (left < right) {
                if (nums[left] + nums[right] > nums[i]) {
                    triangles += right - left;
                    right--;
                } else {
                    left++;
                }
            }
        }

        return triangles;
    }
}
```

### Swift

```swift
class Solution {
    func triangleNumber(_ nums: [Int]) -> Int {
        guard nums.count >= 3 else { return 0 }

        let sortedNums = nums.sorted()
        var triangles = 0

        for i in stride(from: sortedNums.count - 1, through: 2, by: -1) {
            var left = 0
            var right = i - 1

            while left < right {
                if sortedNums[left] + sortedNums[right] > sortedNums[i] {
                    triangles += right - left
                    right -= 1
                } else {
                    left += 1
                }
            }
        }

        return triangles
    }
}

// Example usage
let nums = [2, 2, 3, 4]
let solution = Solution()
print("Number of valid triangles: \(solution.triangleNumber(nums))") // Output: 3
```

### The End