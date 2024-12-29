# Linked List Cycle

## Problem Statement

Given the `head` of a linked list, determine if the linked list has a cycle in it.

## Input

```text
head = [3,2,0,-4], pos = 1
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

bool hasCycle(ListNode? head) {
  ListNode? slow = head;
  ListNode? fast = head;

  while (fast?.next != null) {
    slow = slow?.next;
    fast = fast.next?.next;
    if (slow == fast) return true;
  }

  return false;
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
    public bool HasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast?.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }

        return false;
    }
}
```


### Java

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int x) {
        val = x;
        next = null;
    }
}

public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }

        return false;
    }
}
```


### Kotlin

```kotlin
class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun hasCycle(head: ListNode?): Boolean {
        var slow = head
        var fast = head

        while (fast?.next != null) {
            slow = slow?.next
            fast = fast.next?.next
            if (slow == fast) return true
        }

        return false
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
    func hasCycle(_ head: ListNode?) -> Bool {
        var slow = head
        var fast = head

        while fast?.next != nil {
            slow = slow?.next
            fast = fast?.next?.next
            if slow === fast {
                return true
            }
        }

        return false
    }
}
```


### The End

