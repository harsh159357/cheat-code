# Populating Next Right Pointers in Each Node II

## Problem Statement

Given a binary tree, populate each node's `next` pointer to point to its next right node. If there is no next right node, the `next` pointer should be set to `null`.

You must solve the problem without using extra space (constant space complexity).

## Input

A binary tree root:

```text
        1
      /   \
     2     3
    / \     \
   4   5     7
```

## Output

The tree with populated `next` pointers:

```text
        1 -> NULL
      /   \
     2  -> 3 -> NULL
    / \     \
   4-> 5 ->  7 -> NULL
```


## Solutions

### Dart

```dart
class Node {
  int val;
  Node? left;
  Node? right;
  Node? next;
  
  Node(this.val, {this.left, this.right, this.next});
}

Node? connect(Node? root) {
  if (root == null) return null;

  Node? leftmost = root;

  while (leftmost != null) {
    Node? current = leftmost;
    Node? prev = null;
    leftmost = null;

    while (current != null) {
      if (current.left != null) {
        if (prev != null) {
          prev.next = current.left;
        } else {
          leftmost = current.left;
        }
        prev = current.left;
      }

      if (current.right != null) {
        if (prev != null) {
          prev.next = current.right;
        } else {
          leftmost = current.right;
        }
        prev = current.right;
      }

      current = current.next;
    }
  }

  return root;
}
```


### C#

```csharp
public class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node(int val = 0, Node left = null, Node right = null, Node next = null) {
        this.val = val;
        this.left = left;
        this.right = right;
        this.next = next;
    }
}

public class Solution {
    public Node Connect(Node root) {
        if (root == null) return null;

        Node leftmost = root;

        while (leftmost != null) {
            Node current = leftmost;
            Node prev = null;
            leftmost = null;

            while (current != null) {
                if (current.left != null) {
                    if (prev != null) prev.next = current.left;
                    else leftmost = current.left;
                    prev = current.left;
                }

                if (current.right != null) {
                    if (prev != null) prev.next = current.right;
                    else leftmost = current.right;
                    prev = current.right;
                }

                current = current.next;
            }
        }

        return root;
    }
}
```


### Java

```java
class Node {
    int val;
    Node left;
    Node right;
    Node next;

    Node(int val) {
        this.val = val;
    }
}

class Solution {
    public Node connect(Node root) {
        if (root == null) return null;

        Node leftmost = root;

        while (leftmost != null) {
            Node current = leftmost;
            Node prev = null;
            leftmost = null;

            while (current != null) {
                if (current.left != null) {
                    if (prev != null) {
                        prev.next = current.left;
                    } else {
                        leftmost = current.left;
                    }
                    prev = current.left;
                }

                if (current.right != null) {
                    if (prev != null) {
                        prev.next = current.right;
                    } else {
                        leftmost = current.right;
                    }
                    prev = current.right;
                }

                current = current.next;
            }
        }

        return root;
    }
}
```


### Kotlin

```kotlin
class Node(var `val`: Int) {
    var left: Node? = null
    var right: Node? = null
    var next: Node? = null
}

class Solution {
    fun connect(root: Node?): Node? {
        if (root == null) return null

        var leftmost: Node? = root

        while (leftmost != null) {
            var current: Node? = leftmost
            var prev: Node? = null
            leftmost = null

            while (current != null) {
                if (current.left != null) {
                    if (prev != null) prev.next = current.left else leftmost = current.left
                    prev = current.left
                }
                if (current.right != null) {
                    if (prev != null) prev.next = current.right else leftmost = current.right
                    prev = current.right
                }
                current = current.next
            }
        }

        return root
    }
}
```


### Swift

```swift
class Node {
    var val: Int
    var left: Node?
    var right: Node?
    var next: Node?

    init(_ val: Int) {
        self.val = val
    }
}

class Solution {
    func connect(_ root: Node?) -> Node? {
        guard let root = root else { return nil }

        var leftmost: Node? = root

        while leftmost != nil {
            var current = leftmost
            var prev: Node? = nil
            leftmost = nil

            while current != nil {
                if let left = current?.left {
                    if prev != nil {
                        prev?.next = left
                    } else {
                        leftmost = left
                    }
                    prev = left
                }

                if let right = current?.right {
                    if prev != nil {
                        prev?.next = right
                    } else {
                        leftmost = right
                    }
                    prev = right
                }

                current = current?.next
            }
        }

        return root
    }
}
```


### The End

