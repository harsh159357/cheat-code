# Largest Perimeter Triangle

## Problem Statement

Given an integer array `nums`, return the largest perimeter of a triangle with a non-zero area, formed from three of these lengths. If it is impossible to form any triangle of a non-zero area, return `0`.

## Input

```text
nums = [2,1,2]
```

## Output

```text
5
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun largestPerimeter(nums: IntArray): Int {
        nums.sort()
        for (i in nums.size - 3 downTo 0) {
            if (nums[i] + nums[i + 1] > nums[i + 2]) {
                return nums[i] + nums[i + 1] + nums[i + 2]
            }
        }
        return 0
    }
}
```

### Dart

```dart
int largestPerimeter(List<int> nums) {
  nums.sort();
  for (int i = nums.length - 3; i >= 0; i--) {
    if (nums[i] + nums[i + 1] > nums[i + 2]) {
      return nums[i] + nums[i + 1] + nums[i + 2];
    }
  }
  return 0;
}
```

### C#

```csharp
using System;

public class Solution {
    public int LargestPerimeter(int[] nums) {
        Array.Sort(nums);
        for (int i = nums.Length - 3; i >= 0; i--) {
            if (nums[i] + nums[i + 1] > nums[i + 2]) {
                return nums[i] + nums[i + 1] + nums[i + 2];
            }
        }
        return 0;
    }
}
```

### Java

```java
import java.util.Arrays;

class Solution {
    public int largestPerimeter(int[] nums) {
        Arrays.sort(nums);
        for (int i = nums.length - 3; i >= 0; i--) {
            if (nums[i] + nums[i + 1] > nums[i + 2]) {
                return nums[i] + nums[i + 1] + nums[i + 2];
            }
        }
        return 0;
    }
}
```

### Swift

```swift
class Solution {
    func largestPerimeter(_ nums: [Int]) -> Int {
        let sortedNums = nums.sorted()
        for i in stride(from: sortedNums.count - 3, through: 0, by: -1) {
            if sortedNums[i] + sortedNums[i + 1] > sortedNums[i + 2] {
                return sortedNums[i] + sortedNums[i + 1] + sortedNums[i + 2]
            }
        }
        return 0
    }
}
```

### The End