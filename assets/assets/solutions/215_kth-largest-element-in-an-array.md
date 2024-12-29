# Kth Largest Element in an Array

## Problem Statement

Given an integer array `nums` and an integer `k`, return the `k`th largest element in the array. Note that it is the `k`th largest element in sorted order, not the `k`th distinct element.

## Input

```text
nums = [3,2,1,5,6,4], k = 2
```

## Output

```text
5
```

## Solutions

### Dart

```dart
import 'dart:collection';

int findKthLargest(List<int> nums, int k) {
  PriorityQueue<int> pq = PriorityQueue<int>();
  for (int num in nums) {
    pq.add(num);
    if (pq.length > k) pq.removeFirst();
  }
  return pq.first;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public int FindKthLargest(int[] nums, int k) {
        PriorityQueue<int, int> pq = new PriorityQueue<int, int>();
        foreach (var num in nums) {
            pq.Enqueue(num, num);
            if (pq.Count > k) pq.Dequeue();
        }
        return pq.Peek();
    }
}
```

### Java

```java
import java.util.PriorityQueue;

class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        for (int num : nums) {
            pq.offer(num);
            if (pq.size() > k) {
                pq.poll();
            }
        }
        return pq.peek();
    }
}
```

### Kotlin

```kotlin
import java.util.PriorityQueue

class Solution {
    fun findKthLargest(nums: IntArray, k: Int): Int {
        val pq = PriorityQueue<Int>()
        for (num in nums) {
            pq.offer(num)
            if (pq.size > k) pq.poll()
        }
        return pq.peek()
    }
}
```

### Swift

```swift
import Foundation

class Solution {
    func findKthLargest(_ nums: [Int], _ k: Int) -> Int {
        var pq = Heap<Int>(<)
        for num in nums {
            pq.insert(num)
            if pq.count > k {
                pq.remove()
            }
        }
        return pq.peek() ?? -1
    }
}

class Heap<T: Comparable> {
    var elements: [T] = []
    let sort: (T, T) -> Bool

    init(_ sort: @escaping (T, T) -> Bool) {
        self.sort = sort
    }

    var count: Int { elements.count }

    func insert(_ value: T) {
        elements.append(value)
        swim(elements.count - 1)
    }

    func remove() -> T? {
        guard elements.count > 1 else { return elements.popLast() }
        elements.swapAt(0, elements.count - 1)
        let value = elements.popLast()
        sink(0)
        return value
    }

    func peek() -> T? {
        return elements.first
    }

    private func swim(_ index: Int) {
        var index = index
        while index > 0 {
            let parent = (index - 1) / 2
            if sort(elements[index], elements[parent]) {
                elements.swapAt(index, parent)
                index = parent
            } else {
                break
            }
        }
    }

    private func sink(_ index: Int) {
        var index = index
        let count = elements.count
        while true {
            let left = 2 * index + 1
            let right = 2 * index + 2
            var candidate = index

            if left < count && sort(elements[left], elements[candidate]) {
                candidate = left
            }
            if right < count && sort(elements[right], elements[candidate]) {
                candidate = right
            }
            if candidate == index { break }
            elements.swapAt(index, candidate)
            index = candidate
        }
    }
}
```

### The End

