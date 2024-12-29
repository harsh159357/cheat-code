# Merge Intervals

## Problem Statement

Given an array of intervals where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

## Input

```text
intervals = [[1,3],[2,6],[8,10],[15,18]]
```

## Output

```text
[[1,6],[8,10],[15,18]]  
(Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].)

intervals = [[1,4],[4,5]]
```

## Output

```text
[[1,5]]  
(Explanation: Intervals [1,4] and [4,5] are considered overlapping.)
```

## Solutions

### Dart

```dart
List<List<int>> merge(List<List<int>> intervals) {
  if (intervals.isEmpty) return [];

  intervals.sort((a, b) => a[0].compareTo(b[0]));
  List<List<int>> merged = [];
  List<int> current = intervals[0];

  for (int i = 1; i < intervals.length; i++) {
    if (intervals[i][0] <= current[1]) {
      current[1] = math.max(current[1], intervals[i][1]);
    } else {
      merged.add(current);
      current = intervals[i];
    }
  }

  merged.add(current);
  return merged;
}

void main() {
  print(merge([[1,3],[2,6],[8,10],[15,18]])); // Output: [[1,6],[8,10],[15,18]]
  print(merge([[1,4],[4,5]])); // Output: [[1,5]]
}
```

### C#

```csharp
public class Solution {
    public int[][] Merge(int[][] intervals) {
        if (intervals.Length == 0) return new int[0][];

        Array.Sort(intervals, (a, b) => a[0].CompareTo(b[0]));
        List<int[]> merged = new List<int[]>();
        int[] current = intervals[0];

        foreach (var interval in intervals) {
            if (interval[0] <= current[1]) {
                current[1] = Math.Max(current[1], interval[1]);
            } else {
                merged.Add(current);
                current = interval;
            }
        }

        merged.Add(current);
        return merged.ToArray();
    }
}
```

### Java

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals.length == 0) return new int[0][];

        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        List<int[]> merged = new ArrayList<>();
        int[] current = intervals[0];

        for (int[] interval : intervals) {
            if (interval[0] <= current[1]) {
                current[1] = Math.max(current[1], interval[1]);
            } else {
                merged.add(current);
                current = interval;
            }
        }

        merged.add(current);
        return merged.toArray(new int[merged.size()][]);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun merge(intervals: Array<IntArray>): Array<IntArray> {
        if (intervals.isEmpty()) return emptyArray()

        intervals.sortBy { it[0] }
        val merged = mutableListOf<IntArray>()
        var currentStart = intervals[0][0]
        var currentEnd = intervals[0][1]

        for (i in 1 until intervals.size) {
            val interval = intervals[i]
            if (interval[0] <= currentEnd) {
                currentEnd = maxOf(currentEnd, interval[1])
            } else {
                merged.add(intArrayOf(currentStart, currentEnd))
                currentStart = interval[0]
                currentEnd = interval[1]
            }
        }

        merged.add(intArrayOf(currentStart, currentEnd))
        return merged.toTypedArray()
    }
}
```

### Swift

```swift
class Solution {
    func merge(_ intervals: [[Int]]) -> [[Int]] {
        if intervals.isEmpty { return [] }

        let sortedIntervals = intervals.sorted { $0[0] < $1[0] }
        var merged: [[Int]] = []
        var current = sortedIntervals[0]

        for interval in sortedIntervals {
            if interval[0] <= current[1] {
                current[1] = max(current[1], interval[1])
            } else {
                merged.append(current)
                current = interval
            }
        }

        merged.append(current)
        return merged
    }
}

let solution = Solution()
print(solution.merge([[1,3],[2,6],[8,10],[15,18]])) // Output: [[1,6],[8,10],[15,18]]
print(solution.merge([[1,4],[4,5]])) // Output: [[1,5]]
```

### The End

