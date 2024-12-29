# Remove Duplicates from Sorted List II

## Problem Statement

Given the `head` of a sorted linked list, remove all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.

## Input

```text
head = [1, 2, 3, 3, 4, 4, 5]
```

## Output

```text
[1, 2, 5]
```

(Explanation: Nodes with values 3 and 4 are duplicates and removed.)

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? deleteDuplicates(ListNode? head) {
  ListNode dummy = ListNode(0);
  dummy.next = head;
  ListNode? prev = dummy;
  ListNode? current = head;

  while (current != null) {
    while (current?.next != null && current.val == current.next!.val) {
      current = current.next;
    }

    if (prev?.next == current) {
      prev = prev?.next;
    } else {
      prev?.next = current?.next;
    }

    current = current?.next;
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
    public ListNode DeleteDuplicates(ListNode head) {
        ListNode dummy = new ListNode(0, head);
        ListNode prev = dummy;

        while (head != null) {
            if (head.next != null && head.val == head.next.val) {
                while (head.next != null && head.val == head.next.val) {
                    head = head.next;
                }
                prev.next = head.next;
            } else {
                prev = prev.next;
            }
            head = head.next;
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
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy = new ListNode(0, head);
        ListNode prev = dummy;

        while (head != null) {
            if (head.next != null && head.val == head.next.val) {
                while (head.next != null && head.val == head.next.val) {
                    head = head.next;
                }
                prev.next = head.next;
            } else {
                prev = prev.next;
            }
            head = head.next;
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
    fun deleteDuplicates(head: ListNode?): ListNode? {
        val dummy = ListNode(0)
        dummy.next = head
        var prev: ListNode? = dummy
        var current = head

        while (current != null) {
            while (current?.next != null && current.`val` == current.next!!.`val`) {
                current = current.next
            }

            if (prev?.next == current) {
                prev = prev?.next
            } else {
                prev?.next = current?.next
            }

            current = current?.next
        }

        return dummy.next
    }
}

fun main() {
    val head = ListNode(1).apply {
        next = ListNode(2).apply {
            next = ListNode(3).apply {
                next = ListNode(3).apply {
                    next = ListNode(4).apply {
                        next = ListNode(4).apply {
                            next = ListNode(5)
                        }
                    }
                }
            }
        }
    }

    val result = Solution().deleteDuplicates(head)
    var current = result
    while (current != null) {
        print("${current.`val`} ")
        current = current.next
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
    func deleteDuplicates(_ head: ListNode?) -> ListNode? {
        let dummy = ListNode(0, head)
        var prev: ListNode? = dummy
        var current = head

        while current != nil {
            while current?.next != nil && current!.val == current!.next!.val {
                current = current?.next
            }

            if prev?.next === current {
                prev = prev?.next
            } else {
                prev?.next = current?.next
            }

            current = current?.next
        }

        return dummy.next
    }
}
```

### The End

