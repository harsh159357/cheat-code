
# Merge k Sorted Lists

## Problem Statement

You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order. Merge all the linked-lists into one sorted linked-list and return it.

## Input

```text
lists = [[1, 4, 5], [1, 3, 4], [2, 6]]
```

## Output

```text
[1, 1, 2, 3, 4, 4, 5, 6]
```

## Solutions

### Dart

```dart
import 'dart:collection';

class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? mergeKLists(List<ListNode?> lists) {
  final dummyHead = ListNode(-1);
  var currTail = dummyHead;

  final nodePq = PriorityQueue<ListNode>((a, b) => a.val.compareTo(b.val));
  for (var list in lists) {
    if (list != null) {
      nodePq.add(list);
    }
  }

  while (nodePq.isNotEmpty) {
    final minNode = nodePq.removeFirst();
    if (minNode.next != null) {
      nodePq.add(minNode.next!);
    }
    currTail.next = minNode;
    currTail = minNode;
  }

  return dummyHead.next;
}
```

### C#

```csharp
using System.Collections.Generic;

public class ListNode {
    public int val;
    public ListNode next;
    public ListNode(int val = 0, ListNode next = null) {
        this.val = val;
        this.next = next;
    }
}

public class Solution {
    public ListNode MergeKLists(ListNode[] lists) {
        var dummyHead = new ListNode(-1);
        var currTail = dummyHead;
        var nodePq = new PriorityQueue<ListNode, int>();

        foreach (var list in lists) {
            if (list != null) {
                nodePq.Enqueue(list, list.val);
            }
        }

        while (nodePq.Count > 0) {
            var minNode = nodePq.Dequeue();
            if (minNode.next != null) {
                nodePq.Enqueue(minNode.next, minNode.next.val);
            }
            currTail.next = minNode;
            currTail = minNode;
        }

        return dummyHead.next;
    }
}
```

### Java

```java
import java.util.PriorityQueue;

class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}

class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        PriorityQueue<ListNode> pq = new PriorityQueue<>((a, b) -> Integer.compare(a.val, b.val));

        for (ListNode list : lists) {
            if (list != null) {
                pq.add(list);
            }
        }

        ListNode dummyHead = new ListNode(-1);
        ListNode currTail = dummyHead;

        while (!pq.isEmpty()) {
            ListNode minNode = pq.poll();
            if (minNode.next != null) {
                pq.add(minNode.next);
            }
            currTail.next = minNode;
            currTail = minNode;
        }

        return dummyHead.next;
    }
}
```

### Kotlin

```kotlin
import java.util.PriorityQueue

class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun mergeKLists(lists: Array<ListNode?>): ListNode? {
        val dummyHead = ListNode(-1)
        var currTail = dummyHead

        val nodePq = PriorityQueue<ListNode>(compareBy { it.`val` })
        for (list in lists) {
            list?.let { nodePq.add(it) }
        }

        while (nodePq.isNotEmpty()) {
            val minNode = nodePq.poll()
            minNode.next?.let { nodePq.add(it) }
            currTail.next = minNode
            currTail = minNode
        }

        return dummyHead.next
    }
}
```

### Swift

```swift
import Foundation

public class ListNode {
    public var val: Int
    public var next: ListNode?
    public init() { self.val = 0; self.next = nil; }
    public init(_ val: Int) { self.val = val; self.next = nil; }
    public init(_ val: Int, _ next: ListNode?) { self.val = val; self.next = next; }
}

class Solution {
    func mergeKLists(_ lists: [ListNode?]) -> ListNode? {
        let dummyHead = ListNode(-1)
        var currTail = dummyHead

        let nodePq = PriorityQueue<ListNode> { $0.val < $1.val }
        for list in lists {
            if let list = list {
                nodePq.enqueue(list)
            }
        }

        while !nodePq.isEmpty {
            let minNode = nodePq.dequeue()!
            if let next = minNode.next {
                nodePq.enqueue(next)
            }
            currTail.next = minNode
            currTail = minNode
        }

        return dummyHead.next
    }
}
```

### The End

