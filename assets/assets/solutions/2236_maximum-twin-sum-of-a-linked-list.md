# Maximum Twin Sum of a Linked List

## Problem Statement

In a linked list of size `n`, the `i-th` node (`0 <= i < n/2`) and the `(n-1-i)-th` node are twin nodes.  
The twin sum is defined as the sum of the values of the twin nodes.

Return the maximum twin sum of the linked list.

## Input

```text
head = [5, 4, 2, 1]
```

## Output

```text
6
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
    fun pairSum(head: ListNode?): Int {
        var fast = head
        var slow = head
        val stack = Stack<Int>()
        var sum = 0

        // Traverse to find the midpoint and push the first half values onto the stack
        while (fast != null) {
            stack.push(slow!!.`val`)
            slow = slow.next
            fast = fast.next?.next
        }

        // Compare and calculate twin sums
        while (slow != null) {
            sum = maxOf(sum, stack.pop() + slow.`val`)
            slow = slow.next
        }

        return sum
    }
}

fun main() {
    val head = ListNode(5, ListNode(4, ListNode(2, ListNode(1))))
    println(Solution().pairSum(head)) // Output: 6
}
```

### Dart

```dart
class ListNode {
  int val;
  ListNode? next;
  ListNode(this.val, [this.next]);
}

int pairSum(ListNode? head) {
  ListNode? fast = head, slow = head;
  List<int> stack = [];
  int sum = 0;

  while (fast != null) {
    stack.add(slow!.val);
    slow = slow.next;
    fast = fast.next?.next;
  }

  while (slow != null) {
    sum = max(sum, stack.removeLast() + slow.val);
    slow = slow.next;
  }

  return sum;
}

void main() {
  ListNode head = ListNode(5, ListNode(4, ListNode(2, ListNode(1))));
  print(pairSum(head)); // Output: 6
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
    public int PairSum(ListNode head) {
        ListNode fast = head, slow = head;
        Stack<int> stack = new Stack<int>();
        int sum = 0;

        while (fast != null) {
            stack.Push(slow.val);
            slow = slow.next;
            fast = fast.next?.next;
        }

        while (slow != null) {
            sum = Math.Max(sum, stack.Pop() + slow.val);
            slow = slow.next;
        }

        return sum;
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
    public int pairSum(ListNode head) {
        ListNode fast = head, slow = head;
        Stack<Integer> stack = new Stack<>();
        int sum = 0;

        while (fast != null) {
            stack.push(slow.val);
            slow = slow.next;
            fast = fast.next.next;
        }

        while (slow != null) {
            sum = Math.max(sum, stack.pop() + slow.val);
            slow = slow.next;
        }

        return sum;
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
    func pairSum(_ head: ListNode?) -> Int {
        var fast = head
        var slow = head
        var stack = [Int]()
        var sum = 0

        while fast != nil {
            stack.append(slow!.val)
            slow = slow?.next
            fast = fast?.next?.next
        }

        while slow != nil {
            sum = max(sum, stack.removeLast() + slow!.val)
            slow = slow?.next
        }

        return sum
    }
}

let head = ListNode(5, ListNode(4, ListNode(2, ListNode(1))))
print(Solution().pairSum(head)) // Output: 6
```

### The End