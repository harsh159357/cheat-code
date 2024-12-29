# Sort List

## Problem Statement

Given the head of a linked list, return the list after sorting it in ascending order.

---

## Input

```text
head = [4, 2, 1, 3]
```

---

## Output

```text
[1, 2, 3, 4]
```


## Solutions

### Kotlin

```kotlin
class Solution {

    fun sortList(head: ListNode?): ListNode? {
        if (head?.next == null) return head

        val middlePrec = head.middlePrec
        val middle = middlePrec.next
        middlePrec.next = null

        return merge(sortList(head), sortList(middle))
    }

    private fun merge(lhs: ListNode?, rhs: ListNode?): ListNode? {
        var lhsCurr = lhs
        var rhsCurr = rhs
        val dummyHead = ListNode(0)
        var current: ListNode? = dummyHead

        while (lhsCurr != null && rhsCurr != null) {
            val next = if (rhsCurr.`val` < lhsCurr.`val`) {
                rhsCurr.also { rhsCurr = rhsCurr?.next }
            } else {
                lhsCurr.also { lhsCurr = lhsCurr?.next }
            }

            current?.next = next
            current = next
        }

        if (lhsCurr != null) current?.next = lhsCurr
        if (rhsCurr != null) current?.next = rhsCurr

        return dummyHead.next
    }

    private val ListNode.middlePrec: ListNode
        get() {
            var slow: ListNode? = this
            var fast: ListNode? = this
            while (fast?.next?.next != null) {
                slow = slow?.next
                fast = fast?.next?.next
            }
            return slow ?: this
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

ListNode? sortList(ListNode? head) {
  if (head?.next == null) return head;

  ListNode? middlePrec = getMiddlePrec(head);
  ListNode? middle = middlePrec!.next;
  middlePrec.next = null;

  return merge(sortList(head), sortList(middle));
}

ListNode? merge(ListNode? lhs, ListNode? rhs) {
  ListNode dummyHead = ListNode(0);
  ListNode? current = dummyHead;

  while (lhs != null && rhs != null) {
    if (rhs.val < lhs.val) {
      current!.next = rhs;
      rhs = rhs.next;
    } else {
      current!.next = lhs;
      lhs = lhs.next;
    }
    current = current.next;
  }

  current?.next = lhs ?? rhs;
  return dummyHead.next;
}

ListNode? getMiddlePrec(ListNode? head) {
  ListNode? slow = head;
  ListNode? fast = head;
  while (fast?.next?.next != null) {
    slow = slow?.next;
    fast = fast?.next?.next;
  }
  return slow;
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
    public ListNode SortList(ListNode head) {
        if (head == null || head.next == null) return head;

        ListNode middlePrec = GetMiddlePrec(head);
        ListNode middle = middlePrec.next;
        middlePrec.next = null;

        return Merge(SortList(head), SortList(middle));
    }

    private ListNode Merge(ListNode lhs, ListNode rhs) {
        ListNode dummyHead = new ListNode();
        ListNode current = dummyHead;

        while (lhs != null && rhs != null) {
            if (rhs.val < lhs.val) {
                current.next = rhs;
                rhs = rhs.next;
            } else {
                current.next = lhs;
                lhs = lhs.next;
            }
            current = current.next;
        }

        current.next = lhs ?? rhs;
        return dummyHead.next;
    }

    private ListNode GetMiddlePrec(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast.next?.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
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
    func sortList(_ head: ListNode?) -> ListNode? {
        guard let head = head, head.next != nil else { return head }

        let middlePrec = getMiddlePrec(head)
        let middle = middlePrec.next
        middlePrec.next = nil

        return merge(sortList(head), sortList(middle))
    }

    private func merge(_ lhs: ListNode?, _ rhs: ListNode?) -> ListNode? {
        let dummyHead = ListNode(0)
        var current: ListNode? = dummyHead
        var lhs = lhs
        var rhs = rhs

        while let l = lhs, let r = rhs {
            if r.val < l.val {
                current?.next = r
                rhs = r.next
            } else {
                current?.next = l
                lhs = l.next
            }
            current = current?.next
        }

        current?.next = lhs ?? rhs
        return dummyHead.next
    }

    private func getMiddlePrec(_ head: ListNode) -> ListNode {
        var slow: ListNode? = head
        var fast: ListNode? = head
        while let f = fast?.next?.next {
            slow = slow?.next
            fast = f
        }
        return slow!
    }
}
```

### The End

