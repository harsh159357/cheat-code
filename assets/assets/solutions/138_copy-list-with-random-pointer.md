# Copy List with Random Pointer

## Problem Statement

A linked list of length `n` is given such that each node contains an additional random pointer, which could point to any node in the list or `null`.

Construct a deep copy of the list. The deep copy should consist of exactly `n` brand-new nodes, where each new node has its value set to the value of its corresponding original node. Both the `next` and `random` pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and the copied list represent the same list state.

---

## Input

```text
head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
```

## Output

```text
[[7,null],[13,0],[11,4],[10,2],[1,0]]
```


## Solutions

### Dart

```dart
class Node {
  int val;
  Node? next;
  Node? random;
  Node(this.val, [this.next, this.random]);
}

Node? copyRandomList(Node? head) {
  if (head == null) return null;
  Map<Node, Node> map = {};
  Node? node = head;

  while (node != null) {
    map[node] = Node(node.val);
    node = node.next;
  }

  node = head;
  while (node != null) {
    map[node]?.next = map[node.next];
    map[node]?.random = map[node.random];
    node = node.next;
  }

  return map[head];
}
```

### C#

```csharp
public class Node {
    public int val;
    public Node next;
    public Node random;
    public Node(int _val) {
        val = _val;
        next = null;
        random = null;
    }
}

public class Solution {
    public Node CopyRandomList(Node head) {
        if (head == null) return null;
        Dictionary<Node, Node> map = new Dictionary<Node, Node>();
        Node node = head;

        while (node != null) {
            map[node] = new Node(node.val);
            node = node.next;
        }

        node = head;
        while (node != null) {
            map[node].next = map[node.next];
            map[node].random = map[node.random];
            node = node.next;
        }

        return map[head];
    }
}
```

### Java

```java
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}

class Solution {
    public Node copyRandomList(Node head) {
        if (head == null) return null;
        Map<Node, Node> map = new HashMap<>();
        Node node = head;

        while (node != null) {
            map.put(node, new Node(node.val));
            node = node.next;
        }

        node = head;
        while (node != null) {
            map.get(node).next = map.get(node.next);
            map.get(node).random = map.get(node.random);
            node = node.next;
        }

        return map.get(head);
    }
}
```


### Kotlin

```kotlin
class Node(var `val`: Int) {
    var next: Node? = null
    var random: Node? = null
}

class Solution {
    fun copyRandomList(head: Node?): Node? {
        if (head == null) return null
        val map = mutableMapOf<Node, Node>()
        var node = head

        while (node != null) {
            map[node] = Node(node.`val`)
            node = node.next
        }

        node = head
        while (node != null) {
            map[node]?.next = map[node.next]
            map[node]?.random = map[node.random]
            node = node.next
        }

        return map[head]
    }
}
```


### Swift

```swift
class Node {
    var val: Int
    var next: Node?
    var random: Node?
    init(_ val: Int) {
        self.val = val
        self.next = nil
        self.random = nil
    }
}

class Solution {
    func copyRandomList(_ head: Node?) -> Node? {
        if head == nil { return nil }
        var map: [Node: Node] = [:]
        var node = head

        while let current = node {
            map[current] = Node(current.val)
            node = current.next
        }

        node = head
        while let current = node {
            map[current]?.next = map[current.next]
            map[current]?.random = map[current.random]
            node = current.next
        }

        return map[head]
    }
}
```

### The End

