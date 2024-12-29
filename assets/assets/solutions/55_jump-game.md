# Jump Game

## Problem Statement

You are given an integer array `nums`. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return `true` if you can reach the last index, or `false` otherwise.

## Input

```text
nums = [2, 3, 1, 1, 4]
```

## Output

```text
true  
(Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.)
```

## Input

```text
nums = [3, 2, 1, 0, 4]
```

## Output

## Input

```text
false  
(Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.)
```

## Solutions

### Dart

```dart
bool canJump(List<int> nums) {
  int maxReach = 0;

  for (int i = 0; i < nums.length; i++) {
    if (i > maxReach) return false;
    maxReach = Math.max(maxReach, i + nums[i]);
    if (maxReach >= nums.length - 1) return true;
  }

  return false;
}

void main() {
  print(canJump([2, 3, 1, 1, 4])); // Output: true
  print(canJump([3, 2, 1, 0, 4])); // Output: false
}
```

### C#

```csharp
public class Solution {
    public bool CanJump(int[] nums) {
        int maxReach = 0;

        for (int i = 0; i < nums.Length; i++) {
            if (i > maxReach) return false;
            maxReach = Math.Max(maxReach, i + nums[i]);
            if (maxReach >= nums.Length - 1) return true;
        }

        return false;
    }
}
```

### Java

```java
class Solution {
    public boolean canJump(int[] nums) {
        int maxReach = 0;

        for (int i = 0; i < nums.length; i++) {
            if (i > maxReach) return false;
            maxReach = Math.max(maxReach, i + nums[i]);
            if (maxReach >= nums.length - 1) return true;
        }

        return false;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun canJump(nums: IntArray): Boolean {
        var maxReach = 0

        for (i in nums.indices) {
            if (i > maxReach) return false
            maxReach = maxOf(maxReach, i + nums[i])
            if (maxReach >= nums.size - 1) return true
        }

        return false
    }
}
```

### Swift

```swift
class Solution {
    func canJump(_ nums: [Int]) -> Bool {
        var maxReach = 0

        for i in 0..<nums.count {
            if i > maxReach { return false }
            maxReach = max(maxReach, i + nums[i])
            if maxReach >= nums.count - 1 { return true }
        }

        return false
    }
}

let solution = Solution()
print(solution.canJump([2, 3, 1, 1, 4])) // Output: true
print(solution.canJump([3, 2, 1, 0, 4])) // Output: false
```

### The End

