# Reverse Linked List II

## Problem Statement

Given the `head` of a singly linked list and two integers `left` and `right` where `left <= right`, reverse the nodes of the list from position `left` to position `right`, and return the reversed list.

## Input

```text
head = [1,2,3,4,5], left = 2, right = 4
```

## Output

```text
[1,4,3,2,5]
```

(Explanation: The nodes between positions 2 and 4 are reversed.)

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? reverseBetween(ListNode? head, int left, int right) {
  final dummy = ListNode(0);
  dummy.next = head;
  var pre = dummy;
  for (var i = 1; i < left; i++) {
    pre = pre.next!;
  }
  var cur = pre.next;
  for (var i = left; i < right; i++) {
    final next = cur?.next;
    cur?.next = next?.next;
    next?.next = pre.next;
    pre.next = next;
  }
  return dummy.next;
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
    public ListNode ReverseBetween(ListNode head, int left, int right) {
        var dummy = new ListNode(0, head);
        var pre = dummy;
        for (int i = 1; i < left; i++) {
            pre = pre.next;
        }
        var cur = pre.next;
        for (int i = left; i < right; i++) {
            var next = cur.next;
            cur.next = next.next;
            next.next = pre.next;
            pre.next = next;
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
    ListNode(int val) { this.val = val; this.next = null; }
}

class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        for (int i = 1; i < left; i++) {
            pre = pre.next;
        }
        ListNode cur = pre.next;
        for (int i = left; i < right; i++) {
            ListNode next = cur.next;
            cur.next = next.next;
            next.next = pre.next;
            pre.next = next;
        }
        return dummy.next;
    }
}
```

### Kotlin

```kotlin
class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun reverseBetween(head: ListNode?, left: Int, right: Int): ListNode? {
        val dummy = ListNode(0)
        dummy.next = head
        var pre: ListNode? = dummy
        for (i in 1 until left) {
            pre = pre?.next
        }
        var cur = pre?.next
        for (i in left until right) {
            val next = cur?.next
            cur?.next = next?.next
            next?.next = pre?.next
            pre?.next = next
        }
        return dummy.next
    }
}
```

### Swift

```swift
class ListNode {
    var val: Int
    var next: ListNode?
    init(_ val: Int) {
        self.val = val
        self.next = nil
    }
}

class Solution {
    func reverseBetween(_ head: ListNode?, _ left: Int, _ right: Int) -> ListNode? {
        let dummy = ListNode(0)
        dummy.next = head
        var pre: ListNode? = dummy
        for _ in 1..<left {
            pre = pre?.next
        }
        var cur = pre?.next
        for _ in left..<right {
            let next = cur?.next
            cur?.next = next?.next
            next?.next = pre?.next
            pre?.next = next
        }
        return dummy.next
    }
}
```

### The End

