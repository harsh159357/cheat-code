# Remove Nth Node From End of List

## Problem Statement

Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.

## Input

```text
head = [1, 2, 3, 4, 5], n = 2
```

## Output

```text
[1, 2, 3, 5]
[1, 2, 3, 5]
```

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? removeNthFromEnd(ListNode? head, int n) {
  ListNode dummy = ListNode(0);
  dummy.next = head;
  ListNode? first = dummy;
  ListNode? second = dummy;

  for (int i = 0; i <= n; i++) {
    first = first?.next;
  }

  while (first != null) {
    first = first.next;
    second = second?.next;
  }

  second?.next = second?.next?.next;
  return dummy.next;
}

void main() {
  ListNode head = ListNode(1, ListNode(2, ListNode(3, ListNode(4, ListNode(5)))));
  ListNode? result = removeNthFromEnd(head, 2);

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
    public ListNode RemoveNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0, head);
        ListNode first = dummy;
        ListNode second = dummy;

        for (int i = 0; i <= n; i++) {
            first = first.next;
        }

        while (first != null) {
            first = first.next;
            second = second.next;
        }

        second.next = second.next.next;
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0, head);
        ListNode first = dummy;
        ListNode second = dummy;

        for (int i = 0; i <= n; i++) {
            first = first.next;
        }

        while (first != null) {
            first = first.next;
            second = second.next;
        }

        second.next = second.next.next;
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
    fun removeNthFromEnd(head: ListNode?, n: Int): ListNode? {
        val dummy = ListNode(0)
        dummy.next = head
        var first: ListNode? = dummy
        var second: ListNode? = dummy

        repeat(n + 1) {
            first = first?.next
        }

        while (first != null) {
            first = first.next
            second = second?.next
        }

        second?.next = second?.next?.next
        return dummy.next
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
    func removeNthFromEnd(_ head: ListNode?, _ n: Int) -> ListNode? {
        let dummy = ListNode(0, head)
        var first: ListNode? = dummy
        var second: ListNode? = dummy

        for _ in 0...n {
            first = first?.next
        }

        while first != nil {
            first = first?.next
            second = second?.next
        }

        second?.next = second?.next?.next
        return dummy.next
    }
}
```


### The End

