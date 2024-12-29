# Unique Number of Occurrences

## Problem Statement

Given an array of integers `arr`, return `true` if the number of occurrences of each value in the array is unique, or `false` otherwise.

## Input

```text
arr = [1,2,2,1,1,3]
```

## Output

```text
true
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun uniqueOccurrences(arr: IntArray): Boolean {
        val map = mutableMapOf<Int, Int>()
        for (item in arr) {
            map[item] = map.getOrDefault(item, 0) + 1
        }
        return map.values.toSet().size == map.size
    }
}
```

### Dart

```dart
bool uniqueOccurrences(List<int> arr) {
  Map<int, int> frequency = {};
  for (int num in arr) {
    frequency[num] = (frequency[num] ?? 0) + 1;
  }
  return frequency.values.toSet().length == frequency.length;
}
```

### C#

```csharp
public class Solution {
    public bool UniqueOccurrences(int[] arr) {
        Dictionary<int, int> frequency = new Dictionary<int, int>();
        foreach (int num in arr) {
            if (frequency.ContainsKey(num)) {
                frequency[num]++;
            } else {
                frequency[num] = 1;
            }
        }
        return frequency.Values.Distinct().Count() == frequency.Count;
    }
}
```

### Java

```java
class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        Map<Integer, Integer> frequency = new HashMap<>();
        for (int num : arr) {
            frequency.put(num, frequency.getOrDefault(num, 0) + 1);
        }
        return new HashSet<>(frequency.values()).size() == frequency.size();
    }
}
```

### Swift

```swift
class Solution {
    func uniqueOccurrences(_ arr: [Int]) -> Bool {
        var frequency = [Int: Int]()
        for num in arr {
            frequency[num, default: 0] += 1
        }
        return Set(frequency.values).count == frequency.count
    }
}
```

### The End