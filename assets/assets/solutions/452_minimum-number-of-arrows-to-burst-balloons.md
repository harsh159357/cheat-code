# Minimum Number of Arrows to Burst Balloons

## Problem Statement

You are given an array of `points` where `points[i] = [starti, endi]` represents the start and end of the `i-th` balloon. You can burst a balloon with an arrow if the arrow is shot at a position `x` such that `starti <= x <= endi`. Return the minimum number of arrows required to burst all balloons.

## Input

```text
points = [[10,16], [2,8], [1,6], [7,12]]
```

## Output

```text
2
```

## Solutions

### Dart

```dart
int findMinArrowShots(List<List<int>> points) {
  if (points.isEmpty) return 0;

  // Sort the balloons by their end points
  points.sort((a, b) => a[1].compareTo(b[1]));

  int arrows = 1;
  int end = points[0][1];

  for (int i = 1; i < points.length; i++) {
    if (points[i][0] > end) {
      arrows++;
      end = points[i][1];
    }
  }

  return arrows;
}

void main() {
  print(findMinArrowShots([
    [10, 16],
    [2, 8],
    [1, 6],
    [7, 12]
  ])); // Output: 2
}
```

### C#

```csharp
using System;

public class Solution {
    public int FindMinArrowShots(int[][] points) {
        if (points.Length == 0) return 0;

        // Sort the balloons by their end points
        Array.Sort(points, (a, b) => a[1].CompareTo(b[1]));

        int arrows = 1;
        int end = points[0][1];

        for (int i = 1; i < points.Length; i++) {
            if (points[i][0] > end) {
                arrows++;
                end = points[i][1];
            }
        }

        return arrows;
    }
}
```

### Java

```java
import java.util.Arrays;

class Solution {
    public int findMinArrowShots(int[][] points) {
        if (points.length == 0) return 0;

        // Sort the balloons by their end points
        Arrays.sort(points, (a, b) -> Integer.compare(a[1], b[1]));

        int arrows = 1;
        int end = points[0][1];

        for (int i = 1; i < points.length; i++) {
            if (points[i][0] > end) {
                arrows++;
                end = points[i][1];
            }
        }

        return arrows;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun findMinArrowShots(points: Array<IntArray>): Int {
        if (points.isEmpty()) return 0

        // Sort the balloons by their end points
        points.sortBy { it[1] }

        var arrows = 1
        var end = points[0][1]

        for (i in 1 until points.size) {
            val start = points[i][0]
            if (start > end) {
                arrows++
                end = points[i][1]
            }
        }

        return arrows
    }
}

fun main() {
    val solution = Solution()
    val points1 = arrayOf(intArrayOf(10, 16), intArrayOf(2, 8), intArrayOf(1, 6), intArrayOf(7, 12))
    println("Minimum number of arrows required: ${solution.findMinArrowShots(points1)}") // Output: 2
}
```

### Swift

```swift
class Solution {
    func findMinArrowShots(_ points: [[Int]]) -> Int {
        if points.isEmpty { return 0 }

        let sortedPoints = points.sorted { $0[1] < $1[1] }
        var arrows = 1
        var end = sortedPoints[0][1]

        for i in 1..<sortedPoints.count {
            if sortedPoints[i][0] > end {
                arrows += 1
                end = sortedPoints[i][1]
            }
        }

        return arrows
    }
}

// Example usage
let solution = Solution()
print(solution.findMinArrowShots([[10, 16], [2, 8], [1, 6], [7, 12]])) // Output: 2
```

### The End