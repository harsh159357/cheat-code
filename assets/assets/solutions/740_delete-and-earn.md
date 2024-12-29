# Delete and Earn

## Problem Statement

Given an array `nums` of integers, you can perform the following operation any number of times:

1. Pick any `nums[i]`.
2. Delete `nums[i]` from the array, and also delete every element equal to `nums[i] - 1` and `nums[i] + 1`.

The goal is to maximize the sum of the numbers you pick.

## Input

```text
nums = [3, 4, 2]
```

## Output

```text
6
```


## Solutions

### Dart

```dart
int deleteAndEarn(List<int> nums) {
  if (nums.isEmpty) return 0;

  int maxVal = nums.reduce((a, b) => a > b ? a : b);
  List<int> sumArr = List.filled(maxVal + 1, 0);

  for (var num in nums) {
    sumArr[num] += num;
  }

  int prevSkip = 0, prevTake = sumArr[1];

  for (int i = 2; i <= maxVal; i++) {
    int take = prevSkip + sumArr[i];
    int skip = prevSkip > prevTake ? prevSkip : prevTake;
    prevTake = take;
    prevSkip = skip;
  }

  return prevSkip > prevTake ? prevSkip : prevTake;
}
```

### C#

```csharp
public class Solution {
    public int DeleteAndEarn(int[] nums) {
        if (nums.Length == 0) return 0;

        int maxVal = nums.Max();
        int[] sumArr = new int[maxVal + 1];

        foreach (int num in nums) {
            sumArr[num] += num;
        }

        int prevSkip = 0, prevTake = sumArr[1];

        for (int i = 2; i < sumArr.Length; i++) {
            int take = prevSkip + sumArr[i];
            int skip = Math.Max(prevSkip, prevTake);
            prevTake = take;
            prevSkip = skip;
        }

        return Math.Max(prevSkip, prevTake);
    }
}
```

### Java

```java
class Solution {
    public int deleteAndEarn(int[] nums) {
        if (nums.length == 0) return 0;

        int maxVal = Arrays.stream(nums).max().getAsInt();
        int[] sumArr = new int[maxVal + 1];

        for (int num : nums) {
            sumArr[num] += num;
        }

        int prevSkip = 0, prevTake = sumArr[1];

        for (int i = 2; i <= maxVal; i++) {
            int take = prevSkip + sumArr[i];
            int skip = Math.max(prevSkip, prevTake);
            prevTake = take;
            prevSkip = skip;
        }

        return Math.max(prevSkip, prevTake);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun deleteAndEarn(nums: IntArray): Int {
        if (nums.isEmpty()) return 0

        val maxVal = nums.maxOrNull()!!
        val sumArr = IntArray(maxVal + 1)
        for (num in nums) {
            sumArr[num] += num
        }

        var prevSkip = 0
        var prevTake = sumArr[1]

        for (i in 2 until sumArr.size) {
            val take = prevSkip + sumArr[i]
            val skip = maxOf(prevSkip, prevTake)
            prevTake = take
            prevSkip = skip
        }

        return maxOf(prevSkip, prevTake)
    }
}
```

### Swift

```swift
class Solution {
    func deleteAndEarn(_ nums: [Int]) -> Int {
        if nums.isEmpty { return 0 }

        let maxVal = nums.max()!
        var sumArr = Array(repeating: 0, count: maxVal + 1)

        for num in nums {
            sumArr[num] += num
        }

        var prevSkip = 0
        var prevTake = sumArr[1]

        for i in 2...maxVal {
            let take = prevSkip + sumArr[i]
            let skip = max(prevSkip, prevTake)
            prevTake = take
            prevSkip = skip
        }

        return max(prevSkip, prevTake)
    }
}
```


### The End