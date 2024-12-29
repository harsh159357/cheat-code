# Number of Subsequences That Satisfy the Given Sum Condition

## Problem Statement

Given an array of integers `nums` and an integer `target`, return the number of non-empty subsequences of `nums` such that the sum of the minimum and maximum element on it is less than or equal to `target`. Since the answer may be too large, return it modulo `10^9 + 7`.

## Input

```text
nums = [3, 5, 6, 7]
target = 9
```

## Output

```text
4
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun numSubseq(nums: IntArray, target: Int): Int {
        val MOD = 1_000_000_007
        nums.sort()
        var count = 0
        var left = 0
        var right = nums.size - 1

        val powersOfTwo = IntArray(nums.size)
        powersOfTwo[0] = 1
        for (i in 1 until nums.size) {
            powersOfTwo[i] = powersOfTwo[i - 1] * 2 % MOD
        }

        while (left <= right) {
            if (nums[left] + nums[right] > target) {
                right--
            } else {
                count = (count + powersOfTwo[right - left]) % MOD
                left++
            }
        }
        return count
    }
}
```

### Dart

```dart
int numSubseq(List<int> nums, int target) {
  const MOD = 1000000007;
  nums.sort();
  int count = 0, left = 0, right = nums.length - 1;

  List<int> powersOfTwo = List.filled(nums.length, 1);
  for (int i = 1; i < nums.length; i++) {
    powersOfTwo[i] = (powersOfTwo[i - 1] * 2) % MOD;
  }

  while (left <= right) {
    if (nums[left] + nums[right] > target) {
      right--;
    } else {
      count = (count + powersOfTwo[right - left]) % MOD;
      left++;
    }
  }

  return count;
}
```

### C#

```csharp
public class Solution {
    public int NumSubseq(int[] nums, int target) {
        const int MOD = 1000000007;
        Array.Sort(nums);
        int count = 0, left = 0, right = nums.Length - 1;

        int[] powersOfTwo = new int[nums.Length];
        powersOfTwo[0] = 1;
        for (int i = 1; i < nums.Length; i++) {
            powersOfTwo[i] = (powersOfTwo[i - 1] * 2) % MOD;
        }

        while (left <= right) {
            if (nums[left] + nums[right] > target) {
                right--;
            } else {
                count = (count + powersOfTwo[right - left]) % MOD;
                left++;
            }
        }

        return count;
    }
}
```

### Java

```java
class Solution {
    public int numSubseq(int[] nums, int target) {
        final int MOD = 1_000_000_007;
        Arrays.sort(nums);
        int count = 0, left = 0, right = nums.length - 1;

        int[] powersOfTwo = new int[nums.length];
        powersOfTwo[0] = 1;
        for (int i = 1; i < nums.length; i++) {
            powersOfTwo[i] = (powersOfTwo[i - 1] * 2) % MOD;
        }

        while (left <= right) {
            if (nums[left] + nums[right] > target) {
                right--;
            } else {
                count = (count + powersOfTwo[right - left]) % MOD;
                left++;
            }
        }

        return count;
    }
}
```

### Swift

```swift
class Solution {
    func numSubseq(_ nums: [Int], _ target: Int) -> Int {
        let MOD = 1_000_000_007
        var nums = nums.sorted()
        var count = 0, left = 0, right = nums.count - 1

        var powersOfTwo = [Int](repeating: 1, count: nums.count)
        for i in 1..<nums.count {
            powersOfTwo[i] = (powersOfTwo[i - 1] * 2) % MOD
        }

        while left <= right {
            if nums[left] + nums[right] > target {
                right -= 1
            } else {
                count = (count + powersOfTwo[right - left]) % MOD
                left += 1
            }
        }

        return count
    }
}
```

### The End