# Top K Frequent Elements

## Problem Statement

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements. You may return the answer in any order.

## Input

```text
nums = [1,1,1,2,2,3], k = 2
```

## Output

```text
[1,2]
```

---

## Solutions

### Dart

```dart
List<int> topKFrequent(List<int> nums, int k) {
  Map<int, int> frequencyMap = {};
  for (var num in nums) {
    frequencyMap[num] = (frequencyMap[num] ?? 0) + 1;
  }

  PriorityQueue<int> minHeap = PriorityQueue((a, b) => frequencyMap[a]! - frequencyMap[b]!);

  for (var num in frequencyMap.keys) {
    minHeap.add(num);
    if (minHeap.length > k) {
      minHeap.removeFirst();
    }
  }

  return minHeap.toList();
}
```

### C#

```csharp
using System.Collections.Generic;
using System.Linq;

public class Solution {
    public IList<int> TopKFrequent(int[] nums, int k) {
        var frequencyMap = nums.GroupBy(x => x).ToDictionary(g => g.Key, g => g.Count());
        var minHeap = new SortedSet<(int, int)>((a, b) => a.Item2 == b.Item2 ? a.Item1.CompareTo(b.Item1) : a.Item2.CompareTo(b.Item2));

        foreach (var kvp in frequencyMap) {
            minHeap.Add((kvp.Key, kvp.Value));
            if (minHeap.Count > k) {
                minHeap.Remove(minHeap.First());
            }
        }

        return minHeap.Select(x => x.Item1).ToList();
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> frequencyMap = new HashMap<>();
        for (int num : nums) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }

        PriorityQueue<Integer> minHeap = new PriorityQueue<>((a, b) -> frequencyMap.get(a) - frequencyMap.get(b));

        for (int num : frequencyMap.keySet()) {
            minHeap.offer(num);
            if (minHeap.size() > k) {
                minHeap.poll();
            }
        }

        return new ArrayList<>(minHeap);
    }
}
```

### Kotlin

```kotlin
import java.util.PriorityQueue

class Solution {
    fun topKFrequent(nums: IntArray, k: Int): List<Int> {
        val frequencyMap = mutableMapOf<Int, Int>()
        for (num in nums) {
            frequencyMap[num] = frequencyMap.getOrDefault(num, 0) + 1
        }

        val minHeap = PriorityQueue<Int> { a, b -> frequencyMap[a]!! - frequencyMap[b]!! }

        for (num in frequencyMap.keys) {
            minHeap.offer(num)
            if (minHeap.size > k) {
                minHeap.poll()
            }
        }

        return minHeap.toList()
    }
}
```

### Swift

```swift
import Foundation

class Solution {
    func topKFrequent(_ nums: [Int], _ k: Int) -> [Int] {
        var frequencyMap = [Int: Int]()
        for num in nums {
            frequencyMap[num, default: 0] += 1
        }

        let minHeap = PriorityQueue<(Int, Int)> { $0.1 < $1.1 }

        for (key, value) in frequencyMap {
            minHeap.enqueue((key, value))
            if minHeap.count > k {
                minHeap.dequeue()
            }
        }

        return minHeap.map { $0.0 }
    }
}

public struct PriorityQueue<T> {
    private var elements: [T]
    private let areSorted: (T, T) -> Bool

    public init(_ areSorted: @escaping (T, T) -> Bool) {
        self.elements = []
        self.areSorted = areSorted
    }

    public mutating func enqueue(_ value: T) {
        elements.append(value)
        elements.sort(by: areSorted)
    }

    public mutating func dequeue() -> T? {
        return elements.isEmpty ? nil : elements.removeFirst()
    }

    public func peek() -> T? {
        return elements.first
    }

    public var count: Int {
        return elements.count
    }

    public var isEmpty: Bool {
        return elements.isEmpty
    }
}
```

### The End

