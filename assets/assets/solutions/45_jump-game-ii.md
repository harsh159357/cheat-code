# Jump Game II

## Problem Statement

Given an array of non-negative integers `nums`, you are initially positioned at the first index of the array. Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

You can assume that you can always reach the last index.

## Input

```text
nums = [2,3,1,1,4]
```

## Output

```text
2  
(Explanation: The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.)
```

## Solutions

### Dart

```dart
int jump(List<int> nums) {
  int jumps = 0;
  int currentEnd = 0;
  int farthestReach = 0;

  for (int i = 0; i < nums.length - 1; i++) {
    farthestReach = max(farthestReach, i + nums[i]);

    if (i == currentEnd) {
      jumps++;
      currentEnd = farthestReach;
    }
  }

  return jumps;
}

void main() {
  print(jump([2, 3, 1, 1, 4])); // Output: 2
  print(jump([2, 3, 0, 1, 4])); // Output: 2
}
```

### C#

```csharp
public class Solution {
    public int Jump(int[] nums) {
        int jumps = 0;
        int currentEnd = 0;
        int farthestReach = 0;

        for (int i = 0; i < nums.Length - 1; i++) {
            farthestReach = Math.Max(farthestReach, i + nums[i]);

            if (i == currentEnd) {
                jumps++;
                currentEnd = farthestReach;
            }
        }

        return jumps;
    }
}
```

### Java

```java
class Solution {
    public int jump(int[] nums) {
        int jumps = 0;
        int currentEnd = 0;
        int farthestReach = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            farthestReach = Math.max(farthestReach, i + nums[i]);

            if (i == currentEnd) {
                jumps++;
                currentEnd = farthestReach;
            }
        }

        return jumps;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun jump(nums: IntArray): Int {
        var jumps = 0
        var currentEnd = 0
        var farthestReach = 0

        for (i in 0 until nums.size - 1) {
            farthestReach = maxOf(farthestReach, i + nums[i])

            if (i == currentEnd) {
                jumps++
                currentEnd = farthestReach
            }
        }

        return jumps
    }
}
```

### Swift

```swift
class Solution {
    func jump(_ nums: [Int]) -> Int {
        var jumps = 0
        var currentEnd = 0
        var farthestReach = 0

        for i in 0..<(nums.count - 1) {
            farthestReach = max(farthestReach, i + nums[i])

            if i == currentEnd {
                jumps += 1
                currentEnd = farthestReach
            }
        }

        return jumps
    }
}

let solution = Solution()
print(solution.jump([2, 3, 1, 1, 4])) // Output: 2
print(solution.jump([2, 3, 0, 1, 4])) // Output: 2
```


### The End

