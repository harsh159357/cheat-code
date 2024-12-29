# Russian Doll Envelopes

## Problem Statement

You are given a 2D array of integers `envelopes` where `envelopes[i] = [wᵢ, hᵢ]` represents the width and height of an envelope. One envelope can fit into another if and only if both the width and height of one envelope are greater than the width and height of the other envelope.

Return the maximum number of envelopes you can Russian doll (i.e., put one inside the other).

## Input

```text
envelopes = [[5,4],[6,4],[6,7],[2,3]]
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int maxEnvelopes(List<List<int>> envelopes) {
  envelopes.sort((a, b) => a[0] == b[0] ? b[1] - a[1] : a[0] - b[0]);
  List<int> tops = [];
  
  for (var envelope in envelopes) {
    int height = envelope[1];
    int index = binarySearch(tops, height);
    if (index == tops.length) {
      tops.add(height);
    } else {
      tops[index] = height;
    }
  }
  return tops.length;
}

int binarySearch(List<int> tops, int target) {
  int left = 0, right = tops.length;
  while (left < right) {
    int mid = (left + right) ~/ 2;
    if (tops[mid] >= target) {
      right = mid;
    } else {
      left = mid + 1;
    }
  }
  return left;
}
```

### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public int MaxEnvelopes(int[][] envelopes) {
        Array.Sort(envelopes, (a, b) => a[0] == b[0] ? b[1] - a[1] : a[0] - b[0]);
        var heights = new List<int>();

        foreach (var envelope in envelopes) {
            int height = envelope[1];
            int idx = heights.BinarySearch(height);
            if (idx < 0) idx = ~idx;
            if (idx == heights.Count) heights.Add(height);
            else heights[idx] = height;
        }

        return heights.Count;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int maxEnvelopes(int[][] envelopes) {
        Arrays.sort(envelopes, (a, b) -> a[0] == b[0] ? b[1] - a[1] : a[0] - b[0]);
        int[] dp = new int[envelopes.length];
        int piles = 0;

        for (int[] envelope : envelopes) {
            int height = envelope[1];
            int left = Arrays.binarySearch(dp, 0, piles, height);
            if (left < 0) left = -(left + 1);
            dp[left] = height;
            if (left == piles) piles++;
        }

        return piles;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun maxEnvelopes(envelopes: Array<IntArray>): Int {
        envelopes.sortWith(compareBy({ it[0] }, { -it[1] }))
        val tops = IntArray(envelopes.size)
        var piles = 0

        for (envelope in envelopes) {
            val height = envelope[1]
            val left = findLeft(tops, height, 0, piles)

            if (left == piles) {
                piles++
            }

            tops[left] = height
        }

        return piles
    }

    private fun findLeft(tops: IntArray, k: Int, start: Int, end: Int): Int {
        var lo = start
        var hi = end
        while (lo < hi) {
            val mid = lo + (hi - lo) / 2
            if (tops[mid] >= k) {
                hi = mid
            } else {
                lo = mid + 1
            }
        }
        return lo
    }
}
```

### Swift

```swift
class Solution {
    func maxEnvelopes(_ envelopes: [[Int]]) -> Int {
        let sorted = envelopes.sorted { a, b in
            a[0] == b[0] ? a[1] > b[1] : a[0] < b[0]
        }
        
        var dp = [Int]()
        
        for envelope in sorted {
            let height = envelope[1]
            let idx = dp.binarySearch(height)
            if idx < dp.count {
                dp[idx] = height
            } else {
                dp.append(height)
            }
        }
        
        return dp.count
    }
}

extension Array where Element: Comparable {
    func binarySearch(_ value: Element) -> Int {
        var low = 0
        var high = self.count
        while low < high {
            let mid = low + (high - low) / 2
            if self[mid] >= value {
                high = mid
            } else {
                low = mid + 1
            }
        }
        return low
    }
}
```


### The End

