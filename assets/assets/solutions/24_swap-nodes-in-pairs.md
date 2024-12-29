# Swap Nodes in Pairs

## Problem Statement

Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

## Input

```text
head = [1, 2, 3, 4]
```

## Output

```text
[2, 1, 4, 3]
```

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? swapPairs(ListNode? head) {
  if (head == null || head.next == null) return head;

  ListNode? newHead = head.next;
  head.next = swapPairs(newHead?.next);
  newHead?.next = head;

  return newHead;
}

void main() {
  ListNode head = ListNode(1, ListNode(2, ListNode(3, ListNode(4))));
  ListNode? result = swapPairs(head);

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
    public ListNode SwapPairs(ListNode head) {
        if (head == null || head.next == null) return head;

        ListNode newHead = head.next;
        head.next = SwapPairs(newHead.next);
        newHead.next = head;

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
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) return head;

        ListNode newHead = head.next;
        head.next = swapPairs(newHead.next);
        newHead.next = head;

        return newHead;
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
    fun swapPairs(head: ListNode?): ListNode? {
        if (head == null || head.next == null) return head

        val newHead = head.next
        head.next = swapPairs(newHead?.next)
        newHead?.next = head

        return newHead
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
    func swapPairs(_ head: ListNode?) -> ListNode? {
        guard let head = head, let next = head.next else {
            return head
        }

        let newHead = next
        head.next = swapPairs(next.next)
        newHead.next = head

        return newHead
    }
}
```


### The End

