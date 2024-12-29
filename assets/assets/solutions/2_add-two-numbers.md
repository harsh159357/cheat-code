# Add Two Numbers

## Problem Statement

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Input

```text
l1 = [2, 4, 3]  
l2 = [5, 6, 4]
```

## Output

```text
[7, 0, 8]  
(Explanation: 342 + 465 = 807)
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
  int carry = 0;
  ListNode dummy = ListNode(0);
  ListNode current = dummy;

  while (l1 != null || l2 != null || carry != 0) {
    int sum = (l1?.val ?? 0) + (l2?.val ?? 0) + carry;
    carry = sum ~/ 10;
    current.next = ListNode(sum % 10);
    current = current.next!;
    l1 = l1?.next;
    l2 = l2?.next;
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
    public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = (l1?.val ?? 0) + (l2?.val ?? 0) + carry;
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;
            l1 = l1?.next;
            l2 = l2?.next;
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
    ListNode(int val) { this.val = val; }
}

class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = (l1 != null ? l1.val : 0) + (l2 != null ? l2.val : 0) + carry;
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;
            l1 = (l1 != null) ? l1.next : null;
            l2 = (l2 != null) ? l2.next : null;
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
    fun addTwoNumbers(l1: ListNode?, l2: ListNode?): ListNode? {
        var carry = 0
        var p1 = l1
        var p2 = l2
        val dummy = ListNode(0)
        var current = dummy
        while (p1 != null || p2 != null || carry != 0) {
            val sum = (p1?.`val` ?: 0) + (p2?.`val` ?: 0) + carry
            carry = sum / 10
            current.next = ListNode(sum % 10)
            current = current.next!!
            p1 = p1?.next
            p2 = p2?.next
        }
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
    func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        var carry = 0
        let dummy = ListNode(0)
        var current = dummy
        var p1 = l1
        var p2 = l2

        while p1 != nil || p2 != nil || carry != 0 {
            let sum = (p1?.val ?? 0) + (p2?.val ?? 0) + carry
            carry = sum / 10
            current.next = ListNode(sum % 10)
            current = current.next!
            p1 = p1?.next
            p2 = p2?.next
        }

        return dummy.next
    }
}
```

### The End

