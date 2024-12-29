# Palindrome Linked List

## Problem Statement

Given the `head` of a singly linked list, return `true` if it is a palindrome or `false` otherwise.

## Input

```text
head = [1, 2, 2, 1]
```

## Output

```text
true
```

## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

bool isPalindrome(ListNode? head) {
  if (head == null) return true;

  // Find the middle of the linked list
  ListNode? slow = head, fast = head;
  while (fast?.next != null) {
    slow = slow!.next;
    fast = fast.next!.next;
  }

  // Reverse the second half of the linked list
  ListNode? prev = null, curr = slow;
  while (curr != null) {
    var nextTemp = curr.next;
    curr.next = prev;
    prev = curr;
    curr = nextTemp;
  }

  // Compare the first half with the reversed second half
  ListNode? firstHalf = head, secondHalf = prev;
  while (secondHalf != null) {
    if (firstHalf!.val != secondHalf.val) return false;
    firstHalf = firstHalf.next;
    secondHalf = secondHalf.next;
  }

  return true;
}
```

### C#

```csharp
public class ListNode {
    public int val;
    public ListNode next;
    public ListNode(int x) { val = x; next = null; }
}

public class Solution {
    public bool IsPalindrome(ListNode head) {
        if (head == null) return true;

        // Find the middle of the linked list
        ListNode slow = head, fast = head;
        while (fast?.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Reverse the second half of the linked list
        ListNode prev = null, curr = slow;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
        }

        // Compare the first half with the reversed second half
        ListNode firstHalf = head, secondHalf = prev;
        while (secondHalf != null) {
            if (firstHalf.val != secondHalf.val) return false;
            firstHalf = firstHalf.next;
            secondHalf = secondHalf.next;
        }

        return true;
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
    public boolean isPalindrome(ListNode head) {
        if (head == null) return true;

        // Find the middle of the linked list
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Reverse the second half of the linked list
        ListNode prev = null, curr = slow;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
        }

        // Compare the first half with the reversed second half
        ListNode firstHalf = head, secondHalf = prev;
        while (secondHalf != null) {
            if (firstHalf.val != secondHalf.val) return false;
            firstHalf = firstHalf.next;
            secondHalf = secondHalf.next;
        }

        return true;
    }
}
```

### Kotlin

```kotlin
class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun isPalindrome(head: ListNode?): Boolean {
        if (head == null) return true

        // Find the middle of the linked list
        var slow = head
        var fast = head
        while (fast?.next != null) {
            slow = slow!!.next
            fast = fast.next!!.next
        }

        // Reverse the second half of the linked list
        var prev: ListNode? = null
        var curr = slow
        while (curr != null) {
            val nextTemp = curr.next
            curr.next = prev
            prev = curr
            curr = nextTemp
        }

        // Compare the first half with the reversed second half
        var firstHalf = head
        var secondHalf = prev
        while (secondHalf != null) {
            if (firstHalf!!.`val` != secondHalf.`val`) return false
            firstHalf = firstHalf.next
            secondHalf = secondHalf.next
        }

        return true
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
    func isPalindrome(_ head: ListNode?) -> Bool {
        if head == nil { return true }

        // Find the middle of the linked list
        var slow = head
        var fast = head
        while fast?.next != nil {
            slow = slow?.next
            fast = fast?.next?.next
        }

        // Reverse the second half of the linked list
        var prev: ListNode? = nil
        var curr = slow
        while curr != nil {
            let nextTemp = curr?.next
            curr?.next = prev
            prev = curr
            curr = nextTemp
        }

        // Compare the first half with the reversed second half
        var firstHalf = head
        var secondHalf = prev
        while secondHalf != nil {
            if firstHalf?.val != secondHalf?.val { return false }
            firstHalf = firstHalf?.next
            secondHalf = secondHalf?.next
        }

        return true
    }
}
```

### The End

