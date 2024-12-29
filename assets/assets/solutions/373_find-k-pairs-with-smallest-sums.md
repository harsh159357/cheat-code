# Find K Pairs with Smallest Sums

## Problem Statement

Given two integer arrays `nums1` and `nums2` sorted in ascending order and an integer `k`, return the `k` pairs `(u, v)` with the smallest sums, where `u` is from `nums1` and `v` is from `nums2`.

## Input

```text
nums1 = [1, 7, 11], nums2 = [2, 4, 6], k = 3
```

## Output

```text
[[1, 2], [1, 4], [1, 6]]
```

---

## Solutions

### Dart

```dart
import 'dart:collection';

List<List<int>> kSmallestPairs(List<int> nums1, List<int> nums2, int k) {
  final result = <List<int>>[];
  if (nums1.isEmpty || nums2.isEmpty || k <= 0) return result;

  final pq = PriorityQueue<List<int>>((a, b) => a[0] - b[0]);
  for (int i = 0; i < nums1.length; i++) {
    pq.add([nums1[i] + nums2[0], i, 0]);
  }

  int count = 0;
  while (pq.isNotEmpty && count < k) {
    final pair = pq.removeFirst();
    final i = pair[1];
    final j = pair[2];
    result.add([nums1[i], nums2[j]]);
    if (j < nums2.length - 1) {
      pq.add([nums1[i] + nums2[j + 1], i, j + 1]);
    }
    count++;
  }
  return result;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public IList<IList<int>> KSmallestPairs(int[] nums1, int[] nums2, int k) {
        var result = new List<IList<int>>();
        if (nums1.Length == 0 || nums2.Length == 0 || k <= 0) return result;

        var pq = new PriorityQueue<(int sum, int i, int j), int>();
        for (int i = 0; i < nums1.Length; i++) {
            pq.Enqueue((nums1[i] + nums2[0], i, 0), nums1[i] + nums2[0]);
        }

        while (pq.Count > 0 && k-- > 0) {
            var (sum, i, j) = pq.Dequeue();
            result.Add(new List<int> { nums1[i], nums2[j] });
            if (j < nums2.Length - 1) {
                pq.Enqueue((nums1[i] + nums2[j + 1], i, j + 1), nums1[i] + nums2[j + 1]);
            }
        }
        return result;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public List<List<Integer>> kSmallestPairs(int[] nums1, int[] nums2, int k) {
        List<List<Integer>> result = new ArrayList<>();
        if (nums1.length == 0 || nums2.length == 0 || k <= 0) return result;

        PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[0] - b[0]);
        for (int i = 0; i < nums1.length; i++) {
            pq.offer(new int[] {nums1[i] + nums2[0], i, 0});
        }

        while (!pq.isEmpty() && k-- > 0) {
            int[] pair = pq.poll();
            int i = pair[1], j = pair[2];
            result.add(Arrays.asList(nums1[i], nums2[j]));
            if (j < nums2.length - 1) {
                pq.offer(new int[] {nums1[i] + nums2[j + 1], i, j + 1});
            }
        }
        return result;
    }
}
```

### Kotlin

```kotlin
import java.util.PriorityQueue

class Solution {
    data class Pair(val sum: Int, val i: Int, val j: Int)

    fun kSmallestPairs(nums1: IntArray, nums2: IntArray, k: Int): List<List<Int>> {
        val result = mutableListOf<List<Int>>()
        if (nums1.isEmpty() || nums2.isEmpty() || k <= 0) return result

        val pq = PriorityQueue<Pair> { a, b -> a.sum - b.sum }
        for (i in nums1.indices) {
            pq.offer(Pair(nums1[i] + nums2[0], i, 0))
        }

        var count = 0
        while (pq.isNotEmpty() && count < k) {
            val pair = pq.poll()
            val i = pair.i
            val j = pair.j
            result.add(listOf(nums1[i], nums2[j]))
            if (j < nums2.size - 1) {
                pq.offer(Pair(nums1[i] + nums2[j + 1], i, j + 1))
            }
            count++
        }
        return result
    }
}
```

### Swift

```swift
import Foundation

class Solution {
    func kSmallestPairs(_ nums1: [Int], _ nums2: [Int], _ k: Int) -> [[Int]] {
        var result = [[Int]]()
        if nums1.isEmpty || nums2.isEmpty || k <= 0 { return result }

        var pq = PriorityQueue<(sum: Int, i: Int, j: Int)> { $0.sum < $1.sum }
        for i in 0..<nums1.count {
            pq.enqueue((nums1[i] + nums2[0], i, 0))
        }

        var count = 0
        while !pq.isEmpty && count < k {
            let pair = pq.dequeue()!
            let i = pair.i, j = pair.j
            result.append([nums1[i], nums2[j]])
            if j < nums2.count - 1 {
                pq.enqueue((nums1[i] + nums2[j + 1], i, j + 1))
            }
            count += 1
        }
        return result
    }
}
```

### The End

