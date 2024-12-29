# Find Right Interval

## Problem Statement

You are given an array of `intervals`, where each interval is represented as `[start, end]`. For each interval, find the index of the interval in the array that starts at or after the current interval's end. If no such interval exists, return `-1` for that interval.

Return an array of the indices of the right intervals.

## Input

```text
intervals = [[3, 4], [2, 3], [1, 2]]
```

## Output

```text
[1, 0, -1]
```

## Solutions

### Dart

```dart
import 'dart:collection';

List<int> findRightInterval(List<List<int>> intervals) {
  List<int> result = List.filled(intervals.length, -1);
  Map<int, int> treeMap = SplayTreeMap();

  for (int i = 0; i < intervals.length; i++) {
    treeMap[intervals[i][0]] = i;
  }

  for (int i = 0; i < intervals.length; i++) {
    int? ceilingKey = treeMap.keys.firstWhere(
        (key) => key >= intervals[i][1],
        orElse: () => null);
    if (ceilingKey != null) {
      result[i] = treeMap[ceilingKey]!;
    }
  }

  return result;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public int[] FindRightInterval(int[][] intervals) {
        var result = new int[intervals.Length];
        var treeMap = new SortedDictionary<int, int>();

        for (int i = 0; i < intervals.Length; i++) {
            treeMap[intervals[i][0]] = i;
        }

        for (int i = 0; i < intervals.Length; i++) {
            var ceilingKey = GetCeilingKey(treeMap, intervals[i][1]);
            result[i] = ceilingKey.HasValue ? treeMap[ceilingKey.Value] : -1;
        }

        return result;
    }

    private int? GetCeilingKey(SortedDictionary<int, int> treeMap, int value) {
        foreach (var key in treeMap.Keys) {
            if (key >= value) return key;
        }
        return null;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int[] findRightInterval(int[][] intervals) {
        int[] result = new int[intervals.length];
        TreeMap<Integer, Integer> treeMap = new TreeMap<>();

        for (int i = 0; i < intervals.length; i++) {
            treeMap.put(intervals[i][0], i);
        }

        for (int i = 0; i < intervals.length; i++) {
            Map.Entry<Integer, Integer> entry = treeMap.ceilingEntry(intervals[i][1]);
            result[i] = entry != null ? entry.getValue() : -1;
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun findRightInterval(intervals: Array<IntArray>): IntArray {
        val result = IntArray(intervals.size)
        val treeMap = TreeMap<Int, Int>()

        for ((index, interval) in intervals.withIndex()) {
            treeMap[interval[0]] = index
        }

        for ((index, interval) in intervals.withIndex()) {
            val ceilingKey = treeMap.ceilingKey(interval[1])
            result[index] = if (ceilingKey != null) treeMap[ceilingKey]!! else -1
        }

        return result
    }
}

fun main() {
    val solution = Solution()
    
    val intervals = arrayOf(
        intArrayOf(3, 4),
        intArrayOf(2, 3),
        intArrayOf(1, 2)
    )
    println(solution.findRightInterval(intervals).toList()) // Output: [1, 0, -1]
}
```

### Swift

```swift
class Solution {
    func findRightInterval(_ intervals: [[Int]]) -> [Int] {
        var treeMap = [Int: Int]()
        for (i, interval) in intervals.enumerated() {
            treeMap[interval[0]] = i
        }

        var result = [Int]()
        for interval in intervals {
            let keys = treeMap.keys.sorted()
            if let index = keys.firstIndex(where: { $0 >= interval[1] }) {
                result.append(treeMap[keys[index]]!)
            } else {
                result.append(-1)
            }
        }

        return result
    }
}
```

### The End