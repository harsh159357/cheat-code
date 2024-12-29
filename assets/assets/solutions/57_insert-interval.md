# Insert Interval

## Problem Statement

You are given an array of non-overlapping intervals `intervals` where `intervals[i] = [starti, endi]` represent the start and end of the `i`-th interval and `newInterval = [start, end]` represents a new interval.

Insert `newInterval` into `intervals` such that the intervals remain non-overlapping and sorted in ascending order by start time.

## Input

```text
intervals = [[1,3],[6,9]], newInterval = [2,5]
```

## Output

```text
[[1,5],[6,9]]
```

## Input

```text
intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
```

## Output

```text
[[1,2],[3,10],[12,16]]
```

## Solutions

### Dart

```dart
List<List<int>> insert(List<List<int>> intervals, List<int> newInterval) {
  List<List<int>> result = [];
  int i = 0;

  // Add all intervals that come before the new interval
  while (i < intervals.length && intervals[i][1] < newInterval[0]) {
    result.add(intervals[i]);
    i++;
  }

  // Merge overlapping intervals with the new interval
  List<int> mergedInterval = newInterval;
  while (i < intervals.length && intervals[i][0] <= mergedInterval[1]) {
    mergedInterval[0] = math.min(mergedInterval[0], intervals[i][0]);
    mergedInterval[1] = math.max(mergedInterval[1], intervals[i][1]);
    i++;
  }
  result.add(mergedInterval);

  // Add remaining intervals
  while (i < intervals.length) {
    result.add(intervals[i]);
    i++;
  }

  return result;
}

void main() {
  print(insert([[1,3],[6,9]], [2,5])); // Output: [[1,5],[6,9]]
  print(insert([[1,2],[3,5],[6,7],[8,10],[12,16]], [4,8])); // Output: [[1,2],[3,10],[12,16]]
}
```

### C#

```csharp
public class Solution {
    public int[][] Insert(int[][] intervals, int[] newInterval) {
        List<int[]> result = new List<int[]>();
        int i = 0;

        // Add all intervals that come before the new interval
        while (i < intervals.Length && intervals[i][1] < newInterval[0]) {
            result.Add(intervals[i]);
            i++;
        }

        // Merge overlapping intervals with the new interval
        int[] mergedInterval = newInterval;
        while (i < intervals.Length && intervals[i][0] <= mergedInterval[1]) {
            mergedInterval[0] = Math.Min(mergedInterval[0], intervals[i][0]);
            mergedInterval[1] = Math.Max(mergedInterval[1], intervals[i][1]);
            i++;
        }
        result.Add(mergedInterval);

        // Add remaining intervals
        while (i < intervals.Length) {
            result.Add(intervals[i]);
            i++;
        }

        return result.ToArray();
    }
}
```

### Java

```java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List<int[]> result = new ArrayList<>();
        int i = 0;

        // Add all intervals that come before the new interval
        while (i < intervals.length && intervals[i][1] < newInterval[0]) {
            result.add(intervals[i]);
            i++;
        }

        // Merge overlapping intervals with the new interval
        int[] mergedInterval = newInterval;
        while (i < intervals.length && intervals[i][0] <= mergedInterval[1]) {
            mergedInterval[0] = Math.min(mergedInterval[0], intervals[i][0]);
            mergedInterval[1] = Math.max(mergedInterval[1], intervals[i][1]);
            i++;
        }
        result.add(mergedInterval);

        // Add remaining intervals
        while (i < intervals.length) {
            result.add(intervals[i]);
            i++;
        }

        return result.toArray(new int[result.size()][]);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun insert(intervals: Array<IntArray>, newInterval: IntArray): Array<IntArray> {
        val result = mutableListOf<IntArray>()
        var i = 0
        val n = intervals.size

        // Add all intervals that come before the newInterval
        while (i < n && intervals[i][1] < newInterval[0]) {
            result.add(intervals[i])
            i++
        }

        // Merge intervals that overlap with the newInterval
        var mergedInterval = newInterval.copyOf()
        while (i < n && intervals[i][0] <= newInterval[1]) {
            mergedInterval[0] = minOf(mergedInterval[0], intervals[i][0])
            mergedInterval[1] = maxOf(mergedInterval[1], intervals[i][1])
            i++
        }
        result.add(mergedInterval)

        // Add remaining intervals
        while (i < n) {
            result.add(intervals[i])
            i++
        }

        return result.toTypedArray()
    }
}
```

### Swift

```swift
class Solution {
    func insert(_ intervals: [[Int]], _ newInterval: [Int]) -> [[Int]] {
        var result: [[Int]] = []
        var i = 0
        let n = intervals.count

        // Add all intervals that come before the newInterval
        while i < n && intervals[i][1] < newInterval[0] {
            result.append(intervals[i])
            i += 1
        }

        // Merge intervals that overlap with the newInterval
        var mergedInterval = newInterval
        while i < n && intervals[i][0] <= mergedInterval[1] {
            mergedInterval[0] = min(mergedInterval[0], intervals[i][0])
            mergedInterval[1] = max(mergedInterval[1], intervals[i][1])
            i += 1
        }
        result.append(mergedInterval)

        // Add remaining intervals
        while i < n {
            result.append(intervals[i])
            i += 1
        }

        return result
    }
}

let solution = Solution()
print(solution.insert([[1,3],[6,9]], [2,5])) // Output: [[1,5],[6,9]]
print(solution.insert([[1,2],[3,5],[6,7],[8,10],[12,16]], [4,8])) // Output: [[1,2],[3,10],[12,16]]
```

### The End

