# Find the Longest Valid Obstacle Course at Each Position

## Problem Statement

You are given an array `obstacles` of integers, where `obstacles[i]` represents the height of the `i-th` obstacle. For every position `i`, find the length of the longest obstacle course in non-decreasing order that ends at position `i`.

Return an array `answer`, where `answer[i]` is the length of the longest obstacle course ending with `obstacles[i]`.

## Input

```text
obstacles = [1, 2, 3, 2]
```

## Output

```text
[1, 2, 3, 3]
```

## Solutions

### Kotlin

```kotlin
class Solution {
    private fun bsHelper(list: List<Int>, target: Int, l: Int, r: Int): Int {
        if (l == r) {
            return l
        }
        val m = (l + r) / 2
        return if (list[m] <= target) bsHelper(list, target, m + 1, r) else bsHelper(list, target, l, m)
    }

    fun longestObstacleCourseAtEachPosition(obstacles: IntArray): IntArray {
        val result = IntArray(obstacles.size) { 1 }
        val lnds = mutableListOf(obstacles[0])

        for (i in 1 until obstacles.size) {
            if (obstacles[i] >= lnds.last()) {
                lnds.add(obstacles[i])
                result[i] = lnds.size
            } else {
                val idx = bsHelper(lnds, obstacles[i], 0, lnds.size - 1)
                lnds[idx] = obstacles[i]
                result[i] = idx + 1
            }
        }

        return result
    }
}

fun main() {
    val obstacles = intArrayOf(1, 2, 3, 2)
    println(Solution().longestObstacleCourseAtEachPosition(obstacles).joinToString()) // Output: [1, 2, 3, 3]
}
```

### Dart

```dart
List<int> longestObstacleCourseAtEachPosition(List<int> obstacles) {
  List<int> result = List.filled(obstacles.length, 1);
  List<int> lnds = [obstacles[0]];

  int binarySearch(List<int> list, int target, int left, int right) {
    if (left == right) return left;
    int mid = (left + right) ~/ 2;
    return list[mid] <= target
        ? binarySearch(list, target, mid + 1, right)
        : binarySearch(list, target, left, mid);
  }

  for (int i = 1; i < obstacles.length; i++) {
    if (obstacles[i] >= lnds.last) {
      lnds.add(obstacles[i]);
      result[i] = lnds.length;
    } else {
      int idx = binarySearch(lnds, obstacles[i], 0, lnds.length - 1);
      lnds[idx] = obstacles[i];
      result[i] = idx + 1;
    }
  }

  return result;
}

void main() {
  List<int> obstacles = [1, 2, 3, 2];
  print(longestObstacleCourseAtEachPosition(obstacles)); // Output: [1, 2, 3, 3]
}
```

### C#

```csharp
public class Solution {
    public int[] LongestObstacleCourseAtEachPosition(int[] obstacles) {
        List<int> lnds = new List<int> { obstacles[0] };
        int[] result = new int[obstacles.Length];

        result[0] = 1;

        int BinarySearch(List<int> list, int target) {
            int left = 0, right = list.Count;
            while (left < right) {
                int mid = left + (right - left) / 2;
                if (list[mid] <= target) left = mid + 1;
                else right = mid;
            }
            return left;
        }

        for (int i = 1; i < obstacles.Length; i++) {
            if (obstacles[i] >= lnds[^1]) {
                lnds.Add(obstacles[i]);
                result[i] = lnds.Count;
            } else {
                int idx = BinarySearch(lnds, obstacles[i]);
                lnds[idx] = obstacles[i];
                result[i] = idx + 1;
            }
        }

        return result;
    }
}
```

### Swift

```swift
class Solution {
    func longestObstacleCourseAtEachPosition(_ obstacles: [Int]) -> [Int] {
        var lnds: [Int] = [obstacles[0]]
        var result: [Int] = Array(repeating: 1, count: obstacles.count)

        func binarySearch(_ list: [Int], _ target: Int) -> Int {
            var left = 0, right = list.count
            while left < right {
                let mid = (left + right) / 2
                if list[mid] <= target {
                    left = mid + 1
                } else {
                    right = mid
                }
            }
            return left
        }

        for i in 1..<obstacles.count {
            if obstacles[i] >= lnds.last! {
                lnds.append(obstacles[i])
                result[i] = lnds.count
            } else {
                let idx = binarySearch(lnds, obstacles[i])
                lnds[idx] = obstacles[i]
                result[i] = idx + 1
            }
        }

        return result
    }
}

let obstacles = [1, 2, 3, 2]
print(Solution().longestObstacleCourseAtEachPosition(obstacles)) // Output: [1, 2, 3, 3]
```

### The End