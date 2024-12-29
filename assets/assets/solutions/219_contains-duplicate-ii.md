# Contains Duplicate II

## Problem Statement

Given an integer array `nums` and an integer `k`, return `true` if there are two distinct indices `i` and `j` in the array such that `nums[i] == nums[j]` and the absolute difference between `i` and `j` is at most `k`.

## Input

```text
nums = [1, 2, 3, 1], k = 3
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool containsNearbyDuplicate(List<int> nums, int k) {
  Map<int, int> map = {};
  for (int i = 0; i < nums.length; i++) {
    if (map.containsKey(nums[i]) && (i - map[nums[i]]!) <= k) {
      return true;
    }
    map[nums[i]] = i;
  }
  return false;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public bool ContainsNearbyDuplicate(int[] nums, int k) {
        Dictionary<int, int> map = new Dictionary<int, int>();
        for (int i = 0; i < nums.Length; i++) {
            if (map.ContainsKey(nums[i]) && (i - map[nums[i]]) <= k) {
                return true;
            }
            map[nums[i]] = i;
        }
        return false;
    }
}
```

### Java

```java
import java.util.HashMap;

class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(nums[i]) && (i - map.get(nums[i])) <= k) {
                return true;
            }
            map.put(nums[i], i);
        }
        return false;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun containsNearbyDuplicate(nums: IntArray, k: Int): Boolean {
        val map = HashMap<Int, Int>()
        for (i in nums.indices) {
            if (map.containsKey(nums[i]) && i - map[nums[i]]!! <= k) {
                return true
            }
            map[nums[i]] = i
        }
        return false
    }
}
```

### Swift

```swift
class Solution {
    func containsNearbyDuplicate(_ nums: [Int], _ k: Int) -> Bool {
        var map = [Int: Int]()
        for i in 0..<nums.count {
            if let prevIndex = map[nums[i]], i - prevIndex <= k {
                return true
            }
            map[nums[i]] = i
        }
        return false
    }
}
```


### The End

