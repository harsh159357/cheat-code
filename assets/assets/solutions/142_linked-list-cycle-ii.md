# Linked List Cycle II

## Problem Statement

Given the `head` of a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

## Input

```text
head = [3,2,0,-4], pos = 1
```

## Output

```text
Reference to node with value 2
```


## Solutions

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

ListNode? detectCycle(ListNode? head) {
  ListNode? slow = head;
  ListNode? fast = head;

  while (fast?.next != null) {
    slow = slow?.next;
    fast = fast.next?.next;
    if (slow == fast) {
      slow = head;
      while (slow != fast) {
        slow = slow?.next;
        fast = fast?.next;
      }
      return slow;
    }
  }
  return null;
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
    public ListNode DetectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                slow = head;
                while (slow != fast) {
                    slow = slow.next;
                    fast = fast.next;
                }
                return slow;
            }
        }
        return null;
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
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                slow = head;
                while (slow != fast) {
                    slow = slow.next;
                    fast = fast.next;
                }
                return slow;
            }
        }
        return null;
    }
}
```


### Kotlin

```kotlin
class ListNode(var `val`: Int) {
    var next: ListNode? = null
}

class Solution {
    fun detectCycle(head: ListNode?): ListNode? {
        var slow = head
        var fast = head

        while (fast?.next != null) {
            slow = slow?.next
            fast = fast.next?.next
            if (slow == fast) {
                slow = head
                while (slow != fast) {
                    slow = slow?.next
                    fast = fast?.next
                }
                return slow
            }
        }
        return null
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
    func detectCycle(_ head: ListNode?) -> ListNode? {
        var slow = head
        var fast = head

        while fast?.next != nil {
            slow = slow?.next
            fast = fast?.next?.next

            if slow === fast {
                slow = head
                while slow !== fast {
                    slow = slow?.next
                    fast = fast?.next
                }
                return slow
            }
        }
        return nil
    }
}
```


### The End

