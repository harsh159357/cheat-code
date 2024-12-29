# Find Median from Data Stream

## Problem Statement

The `MedianFinder` class is designed to efficiently calculate the median from a stream of integers. The class supports the following operations:

- `addNum(num)`: Add a number to the data stream.
- `findMedian()`: Return the median of all elements so far.

## Input

```text
Operations: ["MedianFinder", "addNum", "addNum", "findMedian", "addNum", "findMedian"]
Arguments: [[], [1], [2], [], [3], []]
```

## Output

```text
[null, null, null, 1.5, null, 2.0]
```

## Solutions

### Dart

```dart
import 'dart:collection';

class MedianFinder {
  PriorityQueue<int> maxHeap = PriorityQueue((a, b) => b.compareTo(a));
  PriorityQueue<int> minHeap = PriorityQueue();

  void addNum(int num) {
    if (maxHeap.isEmpty || num <= maxHeap.first) {
      maxHeap.add(num);
    } else {
      minHeap.add(num);
    }

    if (maxHeap.length > minHeap.length + 1) {
      minHeap.add(maxHeap.removeFirst());
    } else if (minHeap.length > maxHeap.length) {
      maxHeap.add(minHeap.removeFirst());
    }
  }

  double findMedian() {
    if (maxHeap.length == minHeap.length) {
      return (maxHeap.first + minHeap.first) / 2.0;
    } else {
      return maxHeap.first.toDouble();
    }
  }
}
```

### C#

```csharp
using System.Collections.Generic;

public class MedianFinder {
    private PriorityQueue<int, int> minHeap = new();
    private PriorityQueue<int, int> maxHeap = new((a, b) => b.CompareTo(a));

    public void AddNum(int num) {
        if (maxHeap.Count == 0 || num <= maxHeap.Peek()) {
            maxHeap.Enqueue(num, num);
        } else {
            minHeap.Enqueue(num, num);
        }

        if (maxHeap.Count > minHeap.Count + 1) {
            minHeap.Enqueue(maxHeap.Dequeue(), maxHeap.Dequeue());
        } else if (minHeap.Count > maxHeap.Count) {
            maxHeap.Enqueue(minHeap.Dequeue(), minHeap.Dequeue());
        }
    }

    public double FindMedian() {
        return maxHeap.Count == minHeap.Count
            ? (maxHeap.Peek() + minHeap.Peek()) / 2.0
            : maxHeap.Peek();
    }
}
```

### Java

```java
import java.util.PriorityQueue;

class MedianFinder {
    private PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    private PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a, b) -> b - a);

    public void addNum(int num) {
        if (maxHeap.isEmpty() || num <= maxHeap.peek()) {
            maxHeap.offer(num);
        } else {
            minHeap.offer(num);
        }

        if (maxHeap.size() > minHeap.size() + 1) {
            minHeap.offer(maxHeap.poll());
        } else if (minHeap.size() > maxHeap.size()) {
            maxHeap.offer(minHeap.poll());
        }
    }

    public double findMedian() {
        if (maxHeap.size() == minHeap.size()) {
            return (maxHeap.peek() + minHeap.peek()) / 2.0;
        } else {
            return maxHeap.peek();
        }
    }
}
```

### Kotlin

```kotlin
import java.util.PriorityQueue

class MedianFinder {
    private val minHeap = PriorityQueue<Int>()
    private val maxHeap = PriorityQueue<Int>(Comparator.reverseOrder())

    fun addNum(num: Int) {
        if (maxHeap.isEmpty() || num <= maxHeap.peek()) {
            maxHeap.offer(num)
        } else {
            minHeap.offer(num)
        }
        if (maxHeap.size > minHeap.size + 1) {
            minHeap.offer(maxHeap.poll())
        } else if (minHeap.size > maxHeap.size) {
            maxHeap.offer(minHeap.poll())
        }
    }

    fun findMedian(): Double {
        return if (maxHeap.size == minHeap.size) {
            (maxHeap.peek() + minHeap.peek()) / 2.0
        } else {
            maxHeap.peek().toDouble()
        }
    }
}
```

### Swift

```swift
import Foundation

class MedianFinder {
    private var minHeap: [Int] = []
    private var maxHeap: [Int] = []

    func addNum(_ num: Int) {
        if maxHeap.isEmpty || num <= maxHeap[0] {
            maxHeap.append(num)
            maxHeap.sort(by: >)
        } else {
            minHeap.append(num)
            minHeap.sort(by: <)
        }

        if maxHeap.count > minHeap.count + 1 {
            minHeap.append(maxHeap.removeFirst())
            minHeap.sort(by: <)
        } else if minHeap.count > maxHeap.count {
            maxHeap.append(minHeap.removeFirst())
            maxHeap.sort(by: >)
        }
    }

    func findMedian() -> Double {
        if maxHeap.count == minHeap.count {
            return Double(maxHeap[0] + minHeap[0]) / 2.0
        } else {
            return Double(maxHeap[0])
        }
    }
}
```

### The End

