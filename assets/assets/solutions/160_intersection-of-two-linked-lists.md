# Intersection of Two Linked Lists

## Problem Statement

Write a program to find the node at which the intersection of two singly linked lists begins.

If there is no intersection, return `null`.

### Constraints

- The number of nodes in both lists is in the range `[1, 10^4]`.
- `-10^5 <= Node.val <= 10^5`
- Each list is sorted in ascending order.

---

## Input

```text
headA = [4,1,8,4,5]
headB = [5,6,1,8,4,5]
```

---

## Output

```text
Intersected at '8'
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun getIntersectionNode(headA: ListNode?, headB: ListNode?): ListNode? {
        var pA = headA
        var pB = headB

        // Traverse both lists until they either intersect or reach the end
        while (pA != pB) {
            // Move pointers to the next node
            pA = if (pA != null) pA.next else headB
            pB = if (pB != null) pB.next else headA
        }

        // At this point, either pA is the intersection node or both are null (no intersection)
        return pA
    }
}
```


### Dart

```dart
ListNode? getIntersectionNode(ListNode? headA, ListNode? headB) {
  ListNode? pA = headA;
  ListNode? pB = headB;

  while (pA != pB) {
    pA = (pA != null) ? pA.next : headB;
    pB = (pB != null) ? pB.next : headA;
  }

  return pA;
}
```


### C#

```csharp
public class Solution {
    public ListNode GetIntersectionNode(ListNode headA, ListNode headB) {
        ListNode pA = headA, pB = headB;

        while (pA != pB) {
            pA = (pA != null) ? pA.next : headB;
            pB = (pB != null) ? pB.next : headA;
        }

        return pA;
    }
}
```


### Java

```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode pA = headA, pB = headB;

        while (pA != pB) {
            pA = (pA != null) ? pA.next : headB;
            pB = (pB != null) ? pB.next : headA;
        }

        return pA;
    }
}
```


### Swift

```swift
class Solution {
    func getIntersectionNode(_ headA: ListNode?, _ headB: ListNode?) -> ListNode? {
        var pA = headA
        var pB = headB

        while pA !== pB {
            pA = (pA != nil) ? pA?.next : headB
            pB = (pB != nil) ? pB?.next : headA
        }

        return pA
    }
}
```


### The End

