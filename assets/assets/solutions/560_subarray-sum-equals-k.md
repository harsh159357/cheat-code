# Subarray Sum Equals K

## Problem Statement

Given an array of integers `nums` and an integer `k`, return the total number of continuous subarrays whose sum equals to `k`.

## Input

```text
nums = [1, 1, 1]
k = 2
```

## Output

```text
2
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun subarraySum(nums: IntArray, k: Int): Int {
        var count = 0
        var sum = 0
        val map = mutableMapOf<Int, Int>()
        map[0] = 1 // Base case for an empty subarray

        for (num in nums) {
            sum += num
            val complement = sum - k
            if (map.containsKey(complement)) {
                count += map[complement]!!
            }
            map[sum] = map.getOrDefault(sum, 0) + 1
        }

        return count
    }
}

fun main() {
    val solution = Solution()
    val nums = intArrayOf(1, 1, 1)
    val k = 2
    println("Number of subarrays with sum equal to $k: ${solution.subarraySum(nums, k)}") // Output: 2
}
```

### Dart

```dart
int subarraySum(List<int> nums, int k) {
  int count = 0;
  int sum = 0;
  Map<int, int> map = {0: 1};

  for (int num in nums) {
    sum += num;
    int complement = sum - k;
    if (map.containsKey(complement)) {
      count += map[complement]!;
    }
    map[sum] = (map[sum] ?? 0) + 1;
  }

  return count;
}

void main() {
  print("Number of subarrays with sum equal to 2: ${subarraySum([1, 1, 1], 2)}"); // Output: 2
}
```

### C#

```csharp
public class Solution {
    public int SubarraySum(int[] nums, int k) {
        int count = 0;
        int sum = 0;
        Dictionary<int, int> map = new Dictionary<int, int>();
        map[0] = 1;

        foreach (int num in nums) {
            sum += num;
            int complement = sum - k;
            if (map.ContainsKey(complement)) {
                count += map[complement];
            }
            if (map.ContainsKey(sum)) {
                map[sum]++;
            } else {
                map[sum] = 1;
            }
        }

        return count;
    }
}
```

### Java

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;
        int sum = 0;
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);

        for (int num : nums) {
            sum += num;
            int complement = sum - k;
            if (map.containsKey(complement)) {
                count += map.get(complement);
            }
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }

        return count;
    }
}
```

### Swift

```swift
class Solution {
    func subarraySum(_ nums: [Int], _ k: Int) -> Int {
        var count = 0
        var sum = 0
        var map = [0: 1]

        for num in nums {
            sum += num
            let complement = sum - k
            if let complementCount = map[complement] {
                count += complementCount
            }
            map[sum, default: 0] += 1
        }

        return count
    }
}

// Example usage
let solution = Solution()
print("Number of subarrays with sum equal to 2: \(solution.subarraySum([1, 1, 1], 2))") // Output: 2
```

### The End