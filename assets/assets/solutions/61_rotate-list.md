# Rotate List

## Problem Statement

Given the `head` of a linked list, rotate the list to the right by `k` places.

## Input

```text
head = [1, 2, 3, 4, 5], k = 2
```

## Output

```text
[4, 5, 1, 2, 3]  
(Explanation: Rotating the list to the right by 2 places results in [4, 5, 1, 2, 3].)
```

## Solutions

### Dart

```dartd
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? rotateRight(ListNode? head, int k) {
  if (head == null || head.next == null || k == 0) return head;

  // Calculate the length of the list
  int length = 1;
  ListNode? tail = head;
  while (tail?.next != null) {
    tail = tail.next;
    length++;
  }

  // Find the effective rotations needed
  int rotateTimes = k % length;
  if (rotateTimes == 0) return head;

  // Find the new tail
  ListNode? newTail = head;
  for (int i = 0; i < length - rotateTimes - 1; i++) {
    newTail = newTail?.next;
  }

  // Reconnect the list
  ListNode? newHead = newTail?.next;
  newTail?.next = null;
  tail?.next = head;

  return newHead;
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
    public ListNode RotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) return head;

        // Calculate the length of the list
        int length = 1;
        ListNode tail = head;
        while (tail.next != null) {
            tail = tail.next;
            length++;
        }

        // Find the effective rotations needed
        int rotateTimes = k % length;
        if (rotateTimes == 0) return head;

        // Find the new tail
        ListNode newTail = head;
        for (int i = 0; i < length - rotateTimes - 1; i++) {
            newTail = newTail.next;
        }

        // Reconnect the list
        ListNode newHead = newTail.next;
        newTail.next = null;
        tail.next = head;

        return newHead;
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
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) return head;

        // Calculate the length of the list
        int length = 1;
        ListNode tail = head;
        while (tail.next != null) {
            tail = tail.next;
            length++;
        }

        // Find the effective rotations needed
        int rotateTimes = k % length;
        if (rotateTimes == 0) return head;

        // Find the new tail
        ListNode newTail = head;
        for (int i = 0; i < length - rotateTimes - 1; i++) {
            newTail = newTail.next;
        }

        // Reconnect the list
        ListNode newHead = newTail.next;
        newTail.next = null;
        tail.next = head;

        return newHead;
    }
}
```

### Kotlin

```kotlin
class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun rotateRight(head: ListNode?, k: Int): ListNode? {
        if (head == null || head.next == null || k == 0) return head

        // Calculate the length of the list
        var length = 1
        var tail = head
        while (tail?.next != null) {
            tail = tail.next
            length++
        }

        // Find the effective rotations needed
        val rotateTimes = k % length
        if (rotateTimes == 0) return head

        // Find the new tail
        var newTail = head
        repeat(length - rotateTimes - 1) {
            newTail = newTail?.next
        }

        // Reconnect the list
        val newHead = newTail?.next
        newTail?.next = null
        tail?.next = head

        return newHead
    }
}
```

### Swift

```swift
class ListNode {
    var val: Int
    var next: ListNode?
    init(_ val: Int) { self.val = val; self.next = nil; }
}

class Solution {
    func rotateRight(_ head: ListNode?, _ k: Int) -> ListNode? {
        if head == nil || head?.next == nil || k == 0 { return head }

        // Calculate the length of the list
        var length = 1
        var tail = head
        while tail?.next != nil {
            tail = tail?.next
            length += 1
        }

        // Find the effective rotations needed
        let rotateTimes = k % length
        if rotateTimes == 0 { return head }

        // Find the new tail
        var newTail = head
        for _ in 0..<(length - rotateTimes - 1) {
            newTail = newTail?.next
        }

        // Reconnect the list
        let newHead = newTail?.next
        newTail?.next = nil
        tail?.next = head

        return newHead
    }
}
```

### The End

