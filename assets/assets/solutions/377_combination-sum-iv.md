# Combination Sum IV

## Problem Statement

Given an integer array `nums` with distinct integers and a target integer `target`, return the number of possible combinations that add up to the `target`. The order of numbers in the combinations matters.

## Input

```text
nums = [1, 2, 3], target = 4
```

## Output

```text
7
```

## Solutions

### Dart

```dart
class Solution {
  int combinationSum4(List<int> nums, int target) {
    List<int> dp = List.filled(target + 1, 0);
    dp[0] = 1;

    for (int i = 1; i <= target; i++) {
      for (int num in nums) {
        if (i - num >= 0) {
          dp[i] += dp[i - num];
        }
      }
    }

    return dp[target];
  }
}
```

### C#

```csharp
public class Solution {
    public int CombinationSum4(int[] nums, int target) {
        int[] dp = new int[target + 1];
        dp[0] = 1;

        for (int i = 1; i <= target; i++) {
            foreach (int num in nums) {
                if (i - num >= 0) {
                    dp[i] += dp[i - num];
                }
            }
        }

        return dp[target];
    }
}
```

### Java

```java
class Solution {
    public int combinationSum4(int[] nums, int target) {
        int[] dp = new int[target + 1];
        dp[0] = 1;

        for (int i = 1; i <= target; i++) {
            for (int num : nums) {
                if (i - num >= 0) {
                    dp[i] += dp[i - num];
                }
            }
        }

        return dp[target];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun combinationSum4(nums: IntArray, target: Int): Int {
        val dp = IntArray(target + 1)
        dp[0] = 1

        for (i in 1..target) {
            for (num in nums) {
                if (i - num >= 0) {
                    dp[i] += dp[i - num]
                }
            }
        }

        return dp[target]
    }
}
```

### Swift

```swift
class Solution {
    func combinationSum4(_ nums: [Int], _ target: Int) -> Int {
        var dp = Array(repeating: 0, count: target + 1)
        dp[0] = 1

        for i in 1...target {
            for num in nums {
                if i - num >= 0 {
                    dp[i] += dp[i - num]
                }
            }
        }

        return dp[target]
    }
}
```

---

Let me know if there are any other adjustments or further edits required! 😊


### The End

