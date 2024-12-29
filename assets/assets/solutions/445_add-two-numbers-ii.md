# Add Two Numbers II

## Problem Statement

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except for the number 0 itself.

## Input

```text
l1 = [7, 2, 4, 3]
l2 = [5, 6, 4]
```

## Output

```text
[7, 8, 0, 7]
```

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? addTwoNumbers(ListNode? l1, ListNode? l2) {
  l1 = reverseList(l1);
  l2 = reverseList(l2);

  int carry = 0;
  ListNode? dummy = ListNode(0);
  ListNode? current = dummy;

  while (l1 != null || l2 != null || carry > 0) {
    int sum = (l1?.val ?? 0) + (l2?.val ?? 0) + carry;
    carry = sum ~/ 10;
    current!.next = ListNode(sum % 10);
    current = current.next;

    l1 = l1?.next;
    l2 = l2?.next;
  }

  return reverseList(dummy.next);
}

ListNode? reverseList(ListNode? head) {
  ListNode? prev = null;
  while (head != null) {
    ListNode? next = head.next;
    head.next = prev;
    prev = head;
    head = next;
  }
  return prev;
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
    public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
        l1 = ReverseList(l1);
        l2 = ReverseList(l2);

        int carry = 0;
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;

        while (l1 != null || l2 != null || carry > 0) {
            int sum = (l1?.val ?? 0) + (l2?.val ?? 0) + carry;
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;

            l1 = l1?.next;
            l2 = l2?.next;
        }

        return ReverseList(dummy.next);
    }

    private ListNode ReverseList(ListNode head) {
        ListNode prev = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        l1 = reverseList(l1);
        l2 = reverseList(l2);

        int carry = 0;
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;

        while (l1 != null || l2 != null || carry > 0) {
            int sum = (l1 != null ? l1.val : 0) + (l2 != null ? l2.val : 0) + carry;
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;

            l1 = l1 != null ? l1.next : null;
            l2 = l2 != null ? l2.next : null;
        }

        return reverseList(dummy.next);
    }

    private ListNode reverseList(ListNode head) {
        ListNode prev = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
}
```

### Kotlin

```kotlin
class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun addTwoNumbers(l1: ListNode?, l2: ListNode?): ListNode? {
        val reversedL1 = reverseList(l1)
        val reversedL2 = reverseList(l2)

        var carry = 0
        val dummy = ListNode(0)
        var current = dummy

        var p1 = reversedL1
        var p2 = reversedL2

        while (p1 != null || p2 != null || carry > 0) {
            val sum = (p1?.`val` ?: 0) + (p2?.`val` ?: 0) + carry
            carry = sum / 10
            current.next = ListNode(sum % 10)
            current = current.next!!

            p1 = p1?.next
            p2 = p2?.next
        }

        return reverseList(dummy.next)
    }

    private fun reverseList(head: ListNode?): ListNode? {
        var prev: ListNode? = null
        var current = head

        while (current != null) {
            val nextNode = current.next
            current.next = prev
            prev = current
            current = nextNode
        }

        return prev
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
    func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        let reversedL1 = reverseList(l1)
        let reversedL2 = reverseList(l2)

        var carry = 0
        let dummy = ListNode(0)
        var current: ListNode? = dummy

        var p1 = reversedL1
        var p2 = reversedL2

        while p1 != nil || p2 != nil || carry > 0 {
            let sum = (p1?.val ?? 0) + (p2?.val ?? 0) + carry
            carry = sum / 10
            current?.next = ListNode(sum % 10)
            current = current?.next

            p1 = p1?.next
            p2 = p2?.next
        }

        return reverseList(dummy.next)
    }

    private func reverseList(_ head: ListNode?) -> ListNode? {
        var prev: ListNode? = nil
        var current = head

        while current != nil {
            let nextNode = current?.next
            current?.next = prev
            prev = current
            current = nextNode
        }

        return prev
    }
}
```

### The End