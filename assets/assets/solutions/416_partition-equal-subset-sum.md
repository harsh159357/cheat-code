# Partition Equal Subset Sum

## Problem Statement

Given an integer array `nums`, return `true` if you can partition the array into two subsets such that the sum of the elements in both subsets is equal. Otherwise, return `false`.

## Input

```text
nums = [1, 5, 11, 5]
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool canPartition(List<int> nums) {
  int sum = nums.reduce((a, b) => a + b);
  if (sum % 2 != 0) return false; // If the sum is odd, we can't partition into equal subsets

  int target = sum ~/ 2;
  List<bool> dp = List.filled(target + 1, false);

  dp[0] = true; // Base case: an empty subset can always achieve a sum of 0

  for (int num in nums) {
    for (int j = target; j >= num; j--) {
      dp[j] = dp[j] || dp[j - num];
    }
  }

  return dp[target];
}
```

### C#

```csharp
public class Solution {
    public bool CanPartition(int[] nums) {
        int sum = nums.Sum();
        if (sum % 2 != 0) return false; // If the sum is odd, we can't partition into equal subsets

        int target = sum / 2;
        bool[] dp = new bool[target + 1];

        dp[0] = true; // Base case: an empty subset can always achieve a sum of 0

        foreach (int num in nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }

        return dp[target];
    }
}
```

### Java

```java
class Solution {
    public boolean canPartition(int[] nums) {
        int sum = 0;
        for (int num : nums) {
            sum += num;
        }
        if (sum % 2 != 0) return false; // If the sum is odd, we can't partition into equal subsets

        int target = sum / 2;
        boolean[] dp = new boolean[target + 1];

        dp[0] = true; // Base case: an empty subset can always achieve a sum of 0

        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }

        return dp[target];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun canPartition(nums: IntArray): Boolean {
        val sum = nums.sum()
        if (sum % 2 != 0) return false // If the sum is odd, we can't partition into equal subsets

        val target = sum / 2
        val dp = BooleanArray(target + 1)

        dp[0] = true // Base case: an empty subset can always achieve a sum of 0

        for (num in nums) {
            for (j in target downTo num) {
                dp[j] = dp[j] || dp[j - num]
            }
        }

        return dp[target]
    }
}
```

### Swift

```swift
class Solution {
    func canPartition(_ nums: [Int]) -> Bool {
        let sum = nums.reduce(0, +)
        if sum % 2 != 0 { return false } // If the sum is odd, we can't partition into equal subsets

        let target = sum / 2
        var dp = [Bool](repeating: false, count: target + 1)

        dp[0] = true // Base case: an empty subset can always achieve a sum of 0

        for num in nums {
            for j in stride(from: target, through: num, by: -1) {
                dp[j] = dp[j] || dp[j - num]
            }
        }

        return dp[target]
    }
}
```

### The End