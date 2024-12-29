# Max Number of K-Sum Pairs

## Problem Statement

You are given an integer array `nums` and an integer `k`. In one operation, you can pick two numbers from the array whose sum equals `k` and remove them from the array. Return the maximum number of operations you can perform on the array.

## Input

```text
nums = [1,2,3,4], k = 5
```

## Output

```text
2
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxOperations(nums: IntArray, k: Int): Int {
        val map = mutableMapOf<Int, Int>()
        var count = 0
        for (num in nums) {
            if (map.containsKey(k - num) && map[k - num]!! > 0) {
                count++
                map[k - num] = map[k - num]!! - 1
            } else {
                map[num] = map.getOrDefault(num, 0) + 1
            }
        }
        return count
    }
}

fun main() {
    val nums = intArrayOf(1, 2, 3, 4)
    val k = 5
    println(Solution().maxOperations(nums, k)) // Output: 2
}
```

### Dart

```dart
int maxOperations(List<int> nums, int k) {
  Map<int, int> map = {};
  int count = 0;

  for (int num in nums) {
    if (map.containsKey(k - num) && map[k - num]! > 0) {
      count++;
      map[k - num] = map[k - num]! - 1;
    } else {
      map[num] = (map[num] ?? 0) + 1;
    }
  }

  return count;
}

void main() {
  List<int> nums = [1, 2, 3, 4];
  int k = 5;
  print(maxOperations(nums, k)); // Output: 2
}
```

### C#

```csharp
public class Solution {
    public int MaxOperations(int[] nums, int k) {
        Dictionary<int, int> map = new Dictionary<int, int>();
        int count = 0;

        foreach (int num in nums) {
            if (map.ContainsKey(k - num) && map[k - num] > 0) {
                count++;
                map[k - num]--;
            } else {
                if (!map.ContainsKey(num)) map[num] = 0;
                map[num]++;
            }
        }

        return count;
    }
}
```

### Java

```java
class Solution {
    public int maxOperations(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        int count = 0;

        for (int num : nums) {
            if (map.getOrDefault(k - num, 0) > 0) {
                count++;
                map.put(k - num, map.get(k - num) - 1);
            } else {
                map.put(num, map.getOrDefault(num, 0) + 1);
            }
        }

        return count;
    }
}
```

### Swift

```swift
class Solution {
    func maxOperations(_ nums: [Int], _ k: Int) -> Int {
        var map = [Int: Int]()
        var count = 0

        for num in nums {
            if let value = map[k - num], value > 0 {
                count += 1
                map[k - num]! -= 1
            } else {
                map[num, default: 0] += 1
            }
        }

        return count
    }
}

let nums = [1, 2, 3, 4]
let k = 5
print(Solution().maxOperations(nums, k)) // Output: 2
```

### The End