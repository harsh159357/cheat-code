# Delete the Middle Node of a Linked List

## Problem Statement

You are given the `head` of a singly linked list. Delete the **middle node**, and return the `head` of the modified list.  
If the list has an even number of nodes, the second middle node should be deleted.

## Input

```text
head = [1, 3, 4, 7, 1, 2, 6]
```

## Output

```text
[1, 3, 4, 1, 2, 6]
```

## Solutions

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
    fun deleteMiddle(head: ListNode?): ListNode? {
        // Base case: if there's only one node, return null
        if (head?.next == null) {
            return null
        }

        var prev: ListNode? = null
        var fast = head
        var slow = head

        // Find the middle node using slow and fast pointers
        while (fast?.next != null) {
            prev = slow
            slow = slow?.next
            fast = fast.next?.next
        }

        // Delete the middle node
        prev?.next = slow?.next

        return head
    }
}
```

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? deleteMiddle(ListNode? head) {
  if (head == null || head.next == null) return null;

  ListNode? prev = null;
  ListNode? slow = head;
  ListNode? fast = head;

  while (fast?.next != null) {
    prev = slow;
    slow = slow?.next;
    fast = fast?.next?.next;
  }

  prev?.next = slow?.next;

  return head;
}

void main() {
  // Example: Create linked list 1 -> 3 -> 4 -> 7 -> 1 -> 2 -> 6
  ListNode head = ListNode(1, ListNode(3, ListNode(4, ListNode(7, ListNode(1, ListNode(2, ListNode(6)))))));

  // Delete the middle node
  ListNode? result = deleteMiddle(head);

  // Print the modified list
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
    public ListNode DeleteMiddle(ListNode head) {
        if (head == null || head.next == null) return null;

        ListNode prev = null, slow = head, fast = head;

        while (fast != null && fast.next != null) {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }

        prev.next = slow.next;

        return head;
    }
}
```

### Java

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        if (head == null || head.next == null) return null;

        ListNode prev = null, slow = head, fast = head;

        while (fast != null && fast.next != null) {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }

        prev.next = slow.next;

        return head;
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
    func deleteMiddle(_ head: ListNode?) -> ListNode? {
        if head == nil || head?.next == nil { return nil }

        var prev: ListNode? = nil
        var slow = head
        var fast = head

        while fast?.next != nil {
            prev = slow
            slow = slow?.next
            fast = fast?.next?.next
        }

        prev?.next = slow?.next

        return head
    }
}
```

### The End