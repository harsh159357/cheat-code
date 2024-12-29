# Odd Even Linked List

## Problem Statement

Given a singly linked list, group all odd-indexed nodes together followed by the even-indexed nodes. Note that the relative order inside both the odd and even groups should remain as it was in the input. The first node is considered odd, the second node even, and so on.

Return the reordered list.

## Input

```text
head = [1, 2, 3, 4, 5]
```

## Output

```text
[1, 3, 5, 2, 4]
```

## Solutions

### Dart

```dart
ListNode? oddEvenList(ListNode? head) {
  if (head?.next == null) return head;

  ListNode? odd = head;
  ListNode? even = head.next;
  ListNode? evenHead = even;

  while (even?.next != null) {
    odd?.next = even.next;
    odd = odd?.next;
    even.next = odd?.next;
    even = even.next;
  }

  odd?.next = evenHead;
  return head;
}
```

### C#

```csharp
public class Solution {
    public ListNode OddEvenList(ListNode head) {
        if (head == null || head.next == null) return head;

        ListNode odd = head, even = head.next, evenHead = even;

        while (even?.next != null) {
            odd.next = even.next;
            odd = odd.next;
            even.next = odd.next;
            even = even.next;
        }

        odd.next = evenHead;
        return head;
    }
}
```

### Java

```java
class Solution {
    public ListNode oddEvenList(ListNode head) {
        if (head == null || head.next == null) return head;

        ListNode odd = head, even = head.next, evenHead = even;

        while (even != null && even.next != null) {
            odd.next = even.next;
            odd = odd.next;
            even.next = odd.next;
            even = even.next;
        }

        odd.next = evenHead;
        return head;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun oddEvenList(head: ListNode?): ListNode? {
        if (head?.next == null) return head

        var odd = head
        var even = head.next
        val evenHead = even

        while (even?.next != null) {
            odd?.next = even.next
            odd = odd?.next
            even.next = odd?.next
            even = even.next
        }

        odd?.next = evenHead
        return head
    }
}
```

### Swift

```swift
class Solution {
    func oddEvenList(_ head: ListNode?) -> ListNode? {
        guard let head = head, let even = head.next else {
            return head
        }
        
        var odd: ListNode? = head
        var evenHead: ListNode? = even
        var currentEven: ListNode? = even
        
        while currentEven?.next != nil {
            odd?.next = currentEven?.next
            odd = odd?.next
            currentEven?.next = odd?.next
            currentEven = currentEven?.next
        }
        
        odd?.next = evenHead
        return head
    }
}
```


### The End

