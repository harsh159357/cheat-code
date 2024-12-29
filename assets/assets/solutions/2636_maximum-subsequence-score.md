# Maximum Subsequence Score

## Problem Statement

You are given two integer arrays `nums1` and `nums2` of the same length and an integer `k`.  
Your task is to select exactly `k` indices such that the product of the sum of selected elements from `nums1` and the minimum value of selected elements from `nums2` is maximized.

Return the maximum possible score.

## Input

```text
nums1 = [1, 3, 3, 2]
nums2 = [2, 1, 3, 4]
k = 3
```

## Output

```text
12
```

## Solutions

### Kotlin

```kotlin
import java.util.PriorityQueue

class Solution {
    fun maxScore(nums1: IntArray, nums2: IntArray, k: Int): Long {
        val list = mutableListOf<Pair<Int, Int>>()

        for (i in nums1.indices) {
            list.add(Pair(nums2[i], nums1[i]))
        }

        list.sortByDescending { it.first }

        val pq = PriorityQueue<Int>()
        var sum = 0L
        var result = 0L

        for (i in 0 until k) {
            pq.offer(list[i].second)
            sum += list[i].second
        }

        result = sum * list[k - 1].first

        for (i in k until nums1.size) {
            sum -= pq.poll()
            sum += list[i].second
            pq.offer(list[i].second)

            result = maxOf(result, sum * list[i].first)
        }

        return result
    }
}

fun main() {
    val nums1 = intArrayOf(1, 3, 3, 2)
    val nums2 = intArrayOf(2, 1, 3, 4)
    val k = 3
    println(Solution().maxScore(nums1, nums2, k)) // Output: 12
}
```

### Dart

```dart
import 'dart:collection';

int maxScore(List<int> nums1, List<int> nums2, int k) {
  List<MapEntry<int, int>> list = [];
  for (int i = 0; i < nums1.length; i++) {
    list.add(MapEntry(nums2[i], nums1[i]));
  }

  list.sort((a, b) => b.key.compareTo(a.key));

  PriorityQueue<int> pq = PriorityQueue();
  int sum = 0;
  int result = 0;

  for (int i = 0; i < k; i++) {
    pq.add(list[i].value);
    sum += list[i].value;
  }

  result = sum * list[k - 1].key;

  for (int i = k; i < nums1.length; i++) {
    sum -= pq.removeFirst();
    sum += list[i].value;
    pq.add(list[i].value);

    result = result > sum * list[i].key ? result : sum * list[i].key;
  }

  return result;
}

void main() {
  List<int> nums1 = [1, 3, 3, 2];
  List<int> nums2 = [2, 1, 3, 4];
  int k = 3;
  print(maxScore(nums1, nums2, k)); // Output: 12
}
```


### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public long MaxScore(int[] nums1, int[] nums2, int k) {
        var list = new List<(int, int)>();

        for (int i = 0; i < nums1.Length; i++) {
            list.Add((nums2[i], nums1[i]));
        }

        list.Sort((a, b) => b.Item1.CompareTo(a.Item1));

        var pq = new PriorityQueue<int, int>();
        long sum = 0;
        long result = 0;

        for (int i = 0; i < k; i++) {
            pq.Enqueue(list[i].Item2, list[i].Item2);
            sum += list[i].Item2;
        }

        result = sum * list[k - 1].Item1;

        for (int i = k; i < nums1.Length; i++) {
            sum -= pq.Dequeue();
            sum += list[i].Item2;
            pq.Enqueue(list[i].Item2, list[i].Item2);

            result = Math.Max(result, sum * list[i].Item1);
        }

        return result;
    }
}
```


### Java

```java
import java.util.*;

class Solution {
    public long maxScore(int[] nums1, int[] nums2, int k) {
        List<int[]> list = new ArrayList<>();

        for (int i = 0; i < nums1.length; i++) {
            list.add(new int[] { nums2[i], nums1[i] });
        }

        list.sort((a, b) -> Integer.compare(b[0], a[0]));

        PriorityQueue<Integer> pq = new PriorityQueue<>();
        long sum = 0;
        long result = 0;

        for (int i = 0; i < k; i++) {
            pq.add(list.get(i)[1]);
            sum += list.get(i)[1];
        }

        result = sum * list.get(k - 1)[0];

        for (int i = k; i < nums1.length; i++) {
            sum -= pq.poll();
            sum += list.get(i)[1];
            pq.add(list.get(i)[1]);

            result = Math.max(result, sum * list.get(i)[0]);
        }

        return result;
    }
}
```


### Swift

```swift
class Solution {
    func maxScore(_ nums1: [Int], _ nums2: [Int], _ k: Int) -> Int {
        var list = [(Int, Int)]()
        
        for i in 0..<nums1.count {
            list.append((nums2[i], nums1[i]))
        }

        list.sort(by: { $0.0 > $1.0 })

        var pq = PriorityQueue<Int>()
        var sum = 0
        var result = 0

        for i in 0..<k {
            pq.enqueue(list[i].1)
            sum += list[i].1
        }

        result = sum * list[k - 1].0

        for i in k..<nums1.count {
            sum -= pq.dequeue()!
            sum += list[i].1
            pq.enqueue(list[i].1)

            result = max(result, sum * list[i].0)
        }

        return result
    }
}
```


### The End

