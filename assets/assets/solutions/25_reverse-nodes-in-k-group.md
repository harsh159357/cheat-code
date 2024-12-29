# Reverse Nodes in k-Group

## Problem Statement

Given the `head` of a linked list, reverse the nodes of the list `k` at a time, and return the modified list. Nodes that are not a multiple of `k` at the end should remain in their original order.

## Input

```text
head = [1, 2, 3, 4, 5], k = 2
```

## Output

```text
[2, 1, 4, 3, 5]
```

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? reverseKGroup(ListNode? head, int k) {
  if (head == null || k == 1) return head;

  ListNode dummy = ListNode(-1);
  dummy.next = head;
  ListNode? prevGroupEnd = dummy;

  while (true) {
    ListNode? groupStart = prevGroupEnd?.next;
    ListNode? groupEnd = prevGroupEnd;

    for (int i = 0; i < k && groupEnd != null; i++) {
      groupEnd = groupEnd.next;
    }

    if (groupEnd == null) break;

    ListNode? nextGroupStart = groupEnd.next;
    ListNode? prev = nextGroupStart;
    ListNode? current = groupStart;

    while (current != nextGroupStart) {
      ListNode? temp = current?.next;
      current?.next = prev;
      prev = current;
      current = temp;
    }

    prevGroupEnd?.next = groupEnd;
    prevGroupEnd = groupStart;
  }

  return dummy.next;
}

void main() {
  ListNode head = ListNode(1, ListNode(2, ListNode(3, ListNode(4, ListNode(5)))));
  ListNode? result = reverseKGroup(head, 2);

  while (result != null) {
    print(result.val);
    result = result.next;
  }
}
```

### C#

```csharp
public class ListNode {
    public int val;
    public ListNode next;
    public ListNode(int val = 0, ListNode next = null) {
        this.val = val;
        this.next = next;
    }
}

public class Solution {
    public ListNode ReverseKGroup(ListNode head, int k) {
        if (head == null || k == 1) return head;

        ListNode dummy = new ListNode(-1, head);
        ListNode prevGroupEnd = dummy;

        while (true) {
            ListNode groupStart = prevGroupEnd.next;
            ListNode groupEnd = prevGroupEnd;

            for (int i = 0; i < k && groupEnd != null; i++) {
                groupEnd = groupEnd.next;
            }

            if (groupEnd == null) break;

            ListNode nextGroupStart = groupEnd.next;
            ListNode prev = nextGroupStart;
            ListNode current = groupStart;

            while (current != nextGroupStart) {
                ListNode temp = current.next;
                current.next = prev;
                prev = current;
                current = temp;
            }

            prevGroupEnd.next = groupEnd;
            prevGroupEnd = groupStart;
        }

        return dummy.next;
    }
}
```

### Java

```java
class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}

class Solution {
    public ListNode reverseKGroup(ListNode head, int k) {
        if (head == null || k == 1) return head;

        ListNode dummy = new ListNode(-1, head);
        ListNode prevGroupEnd = dummy;

        while (true) {
            ListNode groupStart = prevGroupEnd.next;
            ListNode groupEnd = prevGroupEnd;

            for (int i = 0; i < k && groupEnd != null; i++) {
                groupEnd = groupEnd.next;
            }

            if (groupEnd == null) break;

            ListNode nextGroupStart = groupEnd.next;
            ListNode prev = nextGroupStart;
            ListNode current = groupStart;

            while (current != nextGroupStart) {
                ListNode temp = current.next;
                current.next = prev;
                prev = current;
                current = temp;
            }

            prevGroupEnd.next = groupEnd;
            prevGroupEnd = groupStart;
        }

        return dummy.next;
    }
}
```

### Kotlin

```kotlin
/**
 * Example:
 * var li = ListNode(5)
 * var v = li.`val`
 * Definition for singly-linked list.
 * class ListNode(var `val`: Int) {
 *     var next: ListNode? = null
 * }
 */
class Solution {
    fun reverseKGroup(head: ListNode?, k: Int): ListNode? {
        val dummy = ListNode(-1)
        dummy.next = head
        var prevGroupEnd: ListNode? = dummy

        while (true) {
            var groupStart = prevGroupEnd?.next
            var groupEnd = prevGroupEnd

            for (i in 0 until k) {
                groupEnd = groupEnd?.next
                if (groupEnd == null) return dummy.next
            }

            val nextGroupStart = groupEnd?.next
            var prev: ListNode? = nextGroupStart
            var current = groupStart

            while (current != nextGroupStart) {
                val temp = current?.next
                current?.next = prev
                prev = current
                current = temp
            }

            prevGroupEnd?.next = groupEnd
            prevGroupEnd = groupStart
        }
    }
}
```

### Swift

```swift
public class ListNode {
    public var val: Int
    public var next: ListNode?
    public init() { self.val = 0; self.next = nil; }
    public init(_ val: Int) { self.val = val; self.next = nil; }
    public init(_ val: Int, _ next: ListNode?) { self.val = val; self.next = next; }
}

class Solution {
    func reverseKGroup(_ head: ListNode?, _ k: Int) -> ListNode? {
        let dummy = ListNode(-1, head)
        var prevGroupEnd: ListNode? = dummy

        while true {
            var groupStart = prevGroupEnd?.next
            var groupEnd = prevGroupEnd

            for _ in 0..<k {
                groupEnd = groupEnd?.next
                if groupEnd == nil { return dummy.next }
            }

            let nextGroupStart = groupEnd?.next
            var prev: ListNode? = nextGroupStart
            var current = groupStart

            while current !== nextGroupStart {
                let temp = current?.next
                current?.next = prev
                prev = current
                current = temp
            }

            prevGroupEnd?.next = groupEnd
            prevGroupEnd = groupStart
        }
    }
}
```

### The End

