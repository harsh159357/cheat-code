# Maximum Average Subarray I

## Problem Statement

Given an integer array `nums` and an integer `k`, find the contiguous subarray of length `k` that has the maximum average value. Return the maximum average value as a double.

## Input

```text
nums = [1, 12, -5, -6, 50, 3], k = 4
```

## Output

```text
12.75
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findMaxAverage(nums: IntArray, k: Int): Double {
        var sum = nums.slice(0 until k).sum()
        var maxSum = sum
        for (i in k until nums.size) {
            sum += nums[i] - nums[i - k]
            maxSum = maxOf(maxSum, sum)
        }
        return maxSum.toDouble() / k
    }
}

fun main() {
    val nums = intArrayOf(1, 12, -5, -6, 50, 3)
    val k = 4
    val solution = Solution()
    println("Maximum average: ${solution.findMaxAverage(nums, k)}") // Output: 12.75
}
```

### Dart

```dart
double findMaxAverage(List<int> nums, int k) {
  int sum = nums.sublist(0, k).reduce((a, b) => a + b);
  int maxSum = sum;

  for (int i = k; i < nums.length; i++) {
    sum += nums[i] - nums[i - k];
    maxSum = maxSum > sum ? maxSum : sum;
  }

  return maxSum / k;
}

void main() {
  List<int> nums = [1, 12, -5, -6, 50, 3];
  int k = 4;
  print("Maximum average: ${findMaxAverage(nums, k)}"); // Output: 12.75
}
```

### C#

```csharp
public class Solution {
    public double FindMaxAverage(int[] nums, int k) {
        int sum = 0;
        for (int i = 0; i < k; i++) {
            sum += nums[i];
        }

        int maxSum = sum;

        for (int i = k; i < nums.Length; i++) {
            sum += nums[i] - nums[i - k];
            maxSum = Math.Max(maxSum, sum);
        }

        return (double)maxSum / k;
    }
}
```

### Java

```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        int sum = 0;
        for (int i = 0; i < k; i++) {
            sum += nums[i];
        }

        int maxSum = sum;

        for (int i = k; i < nums.length; i++) {
            sum += nums[i] - nums[i - k];
            maxSum = Math.max(maxSum, sum);
        }

        return (double) maxSum / k;
    }
}
```

### Swift

```swift
class Solution {
    func findMaxAverage(_ nums: [Int], _ k: Int) -> Double {
        var sum = nums[0..<k].reduce(0, +)
        var maxSum = sum

        for i in k..<nums.count {
            sum += nums[i] - nums[i - k]
            maxSum = max(maxSum, sum)
        }

        return Double(maxSum) / Double(k)
    }
}

// Example usage
let nums = [1, 12, -5, -6, 50, 3]
let k = 4
let solution = Solution()
print("Maximum average: \(solution.findMaxAverage(nums, k))") // Output: 12.75
```

### The End