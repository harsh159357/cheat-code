# Two Sum

## Problem Statement

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## Input

```text
nums = [2, 7, 11, 15]  
target = 9
```

## Output

```text
[0, 1]  
(Because nums[0] + nums[1] = 2 + 7 = 9)
```

## Solutions

### Dart

```dart
List<int> twoSum(List<int> nums, int target) {
  final Map<int, int> map = {};
  for (int i = 0; i < nums.length; i++) {
    final complement = target - nums[i];
    if (map.containsKey(complement)) {
      return [map[complement]!, i];
    }
    map[nums[i]] = i;
  }
  throw Exception("No two sum solution");
}
```

### C#

```csharp
public int[] TwoSum(int[] nums, int target) {
  Dictionary<int, int> map = new Dictionary<int, int>();
  for (int i = 0; i < nums.Length; i++) {
    int complement = target - nums[i];
    if (map.ContainsKey(complement)) {
      return new int[] { map[complement], i };
    }
    map[nums[i]] = i;
  }
  throw new ArgumentException("No two sum solution");
}
```

### Java

```java
class Solution {
  public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
      int complement = target - nums[i];
      if (map.containsKey(complement)) {
        return new int[] { map.get(complement), i };
      }
      map.put(nums[i], i);
    }
    throw new IllegalArgumentException("No two sum solution");
  }
}
```

### Kotlin

```kotlin
fun twoSum(nums: IntArray, target: Int): IntArray {
  val map = mutableMapOf<Int, Int>()
  nums.forEachIndexed { index, num ->
    val complement = target - num
    if (map.containsKey(complement)) {
      return intArrayOf(map[complement]!!, index)
    }
    map[num] = index
  }
  throw IllegalArgumentException("No two sum solution")
}
```

### Swift

```swift
func twoSum(_ nums: [Int], _ target: Int): [Int] {
  var map = [Int: Int]()
  for (index, num) in nums.enumerated() {
    let complement = target - num
    if let complementIndex = map[complement] {
      return [complementIndex, index]
    }
    map[num] = index
  }
  fatalError("No two sum solution")
}
```

### The End