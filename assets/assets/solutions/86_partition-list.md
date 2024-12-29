# Partition List

## Problem Statement

Given the `head` of a linked list and a value `x`, partition it such that all nodes less than `x` come before nodes greater than or equal to `x`.

You should preserve the original relative order of the nodes in each of the two partitions.

## Input

```text
head = [1,4,3,2,5,2], x = 3
```

## Output

```text
[1,2,2,4,3,5]
```

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? partition(ListNode? head, int x) {
  ListNode beforeHead = ListNode(0);
  ListNode afterHead = ListNode(0);
  ListNode before = beforeHead;
  ListNode after = afterHead;

  while (head != null) {
    if (head.val < x) {
      before.next = head;
      before = before.next!;
    } else {
      after.next = head;
      after = after.next!;
    }
    head = head.next;
  }

  after.next = null;
  before.next = afterHead.next;
  return beforeHead.next;
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
    public ListNode Partition(ListNode head, int x) {
        ListNode beforeHead = new ListNode(0);
        ListNode afterHead = new ListNode(0);
        ListNode before = beforeHead;
        ListNode after = afterHead;

        while (head != null) {
            if (head.val < x) {
                before.next = head;
                before = before.next;
            } else {
                after.next = head;
                after = after.next;
            }
            head = head.next;
        }

        after.next = null;
        before.next = afterHead.next;
        return beforeHead.next;
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
    public ListNode partition(ListNode head, int x) {
        ListNode beforeHead = new ListNode(0);
        ListNode afterHead = new ListNode(0);
        ListNode before = beforeHead;
        ListNode after = afterHead;

        while (head != null) {
            if (head.val < x) {
                before.next = head;
                before = before.next;
            } else {
                after.next = head;
                after = after.next;
            }
            head = head.next;
        }

        after.next = null;
        before.next = afterHead.next;
        return beforeHead.next;
    }
}
```

### Kotlin

```kotlin
class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun partition(head: ListNode?, x: Int): ListNode? {
        val beforeHead = ListNode(0)
        val afterHead = ListNode(0)
        var before = beforeHead
        var after = afterHead
        var current = head

        while (current != null) {
            if (current.`val` < x) {
                before.next = current
                before = before.next!!
            } else {
                after.next = current
                after = after.next!!
            }
            current = current.next
        }

        after.next = null
        before.next = afterHead.next
        return beforeHead.next
    }
}

fun main() {
    val head = ListNode(1).apply {
        next = ListNode(4).apply {
            next = ListNode(3).apply {
                next = ListNode(2).apply {
                    next = ListNode(5).apply {
                        next = ListNode(2)
                    }
                }
            }
        }
    }

    val result = Solution().partition(head, 3)
    var current = result
    while (current != null) {
        print("${current.`val`} -> ")
        current = current.next
    }
    println("null")
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
    func partition(_ head: ListNode?, _ x: Int) -> ListNode? {
        let beforeHead = ListNode(0)
        let afterHead = ListNode(0)
        var before: ListNode? = beforeHead
        var after: ListNode? = afterHead
        var current = head

        while current != nil {
            if current!.val < x {
                before?.next = current
                before = before?.next
            } else {
                after?.next = current
                after = after?.next
            }
            current = current?.next
        }

        after?.next = nil
        before?.next = afterHead.next
        return beforeHead.next
    }
}
```

### The End

