# Non-overlapping Intervals

## Problem Statement

Given an array of intervals where `intervals[i] = [starti, endi]`, return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

## Input

```text
intervals = [[1,2],[2,3],[3,4],[1,3]]
```

## Output

```text
1
```

## Solutions

### Dart

```dart
int eraseOverlapIntervals(List<List<int>> intervals) {
  if (intervals.isEmpty) return 0;

  // Sort intervals by their ending times
  intervals.sort((a, b) => a[1].compareTo(b[1]));
  int removed = 0;
  int prevEnd = intervals[0][1];

  for (int i = 1; i < intervals.length; i++) {
    if (intervals[i][0] < prevEnd) {
      removed++;
    } else {
      prevEnd = intervals[i][1];
    }
  }

  return removed;
}
```

### C#

```csharp
using System;

public class Solution {
    public int EraseOverlapIntervals(int[][] intervals) {
        if (intervals.Length == 0) return 0;

        // Sort intervals by their ending times
        Array.Sort(intervals, (a, b) => a[1].CompareTo(b[1]));
        int removed = 0;
        int prevEnd = intervals[0][1];

        for (int i = 1; i < intervals.Length; i++) {
            if (intervals[i][0] < prevEnd) {
                removed++;
            } else {
                prevEnd = intervals[i][1];
            }
        }

        return removed;
    }
}
```

### Java

```java
import java.util.Arrays;

class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        if (intervals.length == 0) return 0;

        // Sort intervals by their ending times
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[1], b[1]));
        int removed = 0;
        int prevEnd = intervals[0][1];

        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] < prevEnd) {
                removed++;
            } else {
                prevEnd = intervals[i][1];
            }
        }

        return removed;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun eraseOverlapIntervals(intervals: Array<IntArray>): Int {
        if (intervals.isEmpty()) return 0

        // Sort intervals by their ending times
        intervals.sortBy { it[1] }
        var removed = 0
        var prevEnd = intervals[0][1]

        for (i in 1 until intervals.size) {
            if (intervals[i][0] < prevEnd) {
                removed++
            } else {
                prevEnd = intervals[i][1]
            }
        }

        return removed
    }
}
```

### Swift

```swift
class Solution {
    func eraseOverlapIntervals(_ intervals: [[Int]]) -> Int {
        if intervals.isEmpty { return 0 }

        // Sort intervals by their ending times
        let sortedIntervals = intervals.sorted { $0[1] < $1[1] }
        var removed = 0
        var prevEnd = sortedIntervals[0][1]

        for i in 1..<sortedIntervals.count {
            if sortedIntervals[i][0] < prevEnd {
                removed += 1
            } else {
                prevEnd = sortedIntervals[i][1]
            }
        }

        return removed
    }
}
```

### The End