# Maximum Subarray

## Problem Statement

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

## Input

```text
nums = [-2,1,-3,4,-1,2,1,-5,4]
```

## Output

```text
6  
(Explanation: [4,-1,2,1] has the largest sum = 6.)
```

## Solutions

### Dart

```dart
int maxSubArray(List<int> nums) {
  int maxEndingHere = nums[0];
  int maxSoFar = nums[0];

  for (int i = 1; i < nums.length; i++) {
    maxEndingHere = Math.max(nums[i], maxEndingHere + nums[i]);
    maxSoFar = Math.max(maxSoFar, maxEndingHere);
  }

  return maxSoFar;
}

void main() {
  print(maxSubArray([-2,1,-3,4,-1,2,1,-5,4])); // Output: 6
}
```

### C#

```csharp
public class Solution {
    public int MaxSubArray(int[] nums) {
        int maxEndingHere = nums[0];
        int maxSoFar = nums[0];

        for (int i = 1; i < nums.Length; i++) {
            maxEndingHere = Math.Max(nums[i], maxEndingHere + nums[i]);
            maxSoFar = Math.Max(maxSoFar, maxEndingHere);
        }

        return maxSoFar;
    }
}
```

### Java

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxEndingHere = nums[0];
        int maxSoFar = nums[0];

        for (int i = 1; i < nums.length; i++) {
            maxEndingHere = Math.max(nums[i], maxEndingHere + nums[i]);
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }

        return maxSoFar;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun maxSubArray(nums: IntArray): Int {
        var maxEndingHere = nums[0]
        var maxSoFar = nums[0]

        for (i in 1 until nums.size) {
            maxEndingHere = maxOf(nums[i], maxEndingHere + nums[i])
            maxSoFar = maxOf(maxSoFar, maxEndingHere)
        }

        return maxSoFar
    }
}
```

### Swift

```swift
class Solution {
    func maxSubArray(_ nums: [Int]) -> Int {
        var maxEndingHere = nums[0]
        var maxSoFar = nums[0]

        for i in 1..<nums.count {
            maxEndingHere = max(nums[i], maxEndingHere + nums[i])
            maxSoFar = max(maxSoFar, maxEndingHere)
        }

        return maxSoFar
    }
}

let solution = Solution()
print(solution.maxSubArray([-2,1,-3,4,-1,2,1,-5,4])) // Output: 6
```

### The End

