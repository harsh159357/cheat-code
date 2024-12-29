# Reverse Linked List

## Problem Statement

Given the `head` of a singly linked list, reverse the list and return its new head.

## Input

```text
head = [1,2,3,4,5]
```

## Output

```text
[5,4,3,2,1]
```

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? reverseList(ListNode? head) {
  ListNode? prev = null;
  ListNode? curr = head;
  while (curr != null) {
    ListNode? nextTemp = curr.next;
    curr.next = prev;
    prev = curr;
    curr = nextTemp;
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
    public ListNode ReverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
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
    ListNode(int val) { this.val = val; }
}

class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
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
    fun reverseList(head: ListNode?): ListNode? {
        var prev: ListNode? = null
        var curr = head
        while (curr != null) {
            val nextTemp = curr.next
            curr.next = prev
            prev = curr
            curr = nextTemp
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
    init(_ val: Int, _ next: ListNode? = nil) {
        self.val = val
        self.next = next
    }
}

class Solution {
    func reverseList(_ head: ListNode?) -> ListNode? {
        var prev: ListNode? = nil
        var curr = head
        while curr != nil {
            let nextTemp = curr?.next
            curr?.next = prev
            prev = curr
            curr = nextTemp
        }
        return prev
    }
}
```



### The End

