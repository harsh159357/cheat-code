# Number of Recent Calls

## Problem Statement

Design a class `RecentCounter` to count recent requests.

You have one method:

- `ping(int t)`:

    - Adds a new request at time `t`.
    - Returns the number of requests that have been made in the past `3000` milliseconds (including the new request).

## Input

```text
["RecentCounter", "ping", "ping", "ping", "ping"]
[[], [1], [100], [3001], [3002]]
```

## Output

```text
[null, 1, 2, 3, 3]
```

## Solutions

### Kotlin

```kotlin
class RecentCounter {

    private val queue = LinkedList<Int>()

    fun ping(t: Int): Int {
        queue.offer(t)
        while (queue.peek() < t - 3000) {
            queue.poll()
        }
        return queue.size
    }
}

/**
 * Your RecentCounter object will be instantiated and called as such:
 * var obj = RecentCounter()
 * var param_1 = obj.ping(t)
 */
```

### Dart

```dart
class RecentCounter {
  final Queue<int> queue = Queue();

  int ping(int t) {
    queue.add(t);
    while (queue.isNotEmpty && queue.first < t - 3000) {
      queue.removeFirst();
    }
    return queue.length;
  }
}

/**
 * var obj = RecentCounter();
 * var param_1 = obj.ping(t);
 */
```

### C#

```csharp
using System.Collections.Generic;

public class RecentCounter {
    private Queue<int> queue;

    public RecentCounter() {
        queue = new Queue<int>();
    }

    public int Ping(int t) {
        queue.Enqueue(t);
        while (queue.Peek() < t - 3000) {
            queue.Dequeue();
        }
        return queue.Count;
    }
}

/**
 * RecentCounter obj = new RecentCounter();
 * int param_1 = obj.Ping(t);
 */
```

### Java

```java
import java.util.LinkedList;
import java.util.Queue;

class RecentCounter {
    private Queue<Integer> queue;

    public RecentCounter() {
        queue = new LinkedList<>();
    }

    public int ping(int t) {
        queue.offer(t);
        while (queue.peek() < t - 3000) {
            queue.poll();
        }
        return queue.size();
    }
}

/**
 * RecentCounter obj = new RecentCounter();
 * int param_1 = obj.ping(t);
 */
```

### Swift

```swift
class RecentCounter {

    private var queue = [Int]()

    func ping(_ t: Int) -> Int {
        queue.append(t)
        while queue.first! < t - 3000 {
            queue.removeFirst()
        }
        return queue.count
    }
}

/**
 * let obj = RecentCounter()
 * let ret_1: Int = obj.ping(t)
 */
```

### The End