# Binary Search Tree Iterator

## Problem Statement

Implement the `BSTIterator` class that represents an iterator over a binary search tree (BST):

- `BSTIterator(TreeNode root)` Initializes an object of the BSTIterator class. The root of the BST is given as part of the constructor. The pointer is initialized to a non-existent number smaller than any element in the BST.
- `Int next()` Moves the pointer to the next smallest number and returns it.
- `Boolean hasNext()` Returns `true` if there exists a next number in the iterator, otherwise returns `false`.

You must implement the class such that calls to `next()` and `hasNext()` run in **amortized O(1)** time complexity and use O(h) memory, where h is the height of the tree.

---

## Input

```text
["BSTIterator", "next", "next", "hasNext", "next", "hasNext", "next", "hasNext", "next", "hasNext"]
[[[7, 3, 15, null, null, 9, 20]], [], [], [], [], [], [], [], [], []]
```

## Output

```text
[null, 3, 7, true, 9, true, 15, true, 20, false]
```


## Solutions

### Kotlin

```kotlin
class BSTIterator(root: TreeNode?) {
    private val stack = LinkedList<TreeNode>()

    init {
        pushAllLeft(root)
    }

    private fun pushAllLeft(node: TreeNode?) {
        var current = node
        while (current != null) {
            stack.push(current)
            current = current.left
        }
    }

    fun next(): Int {
        val node = stack.pop()
        if (node.right != null) {
            pushAllLeft(node.right)
        }
        return node.`val`
    }

    fun hasNext(): Boolean {
        return stack.isNotEmpty()
    }
}
```


### Dart

```dart
class BSTIterator {
  final List<TreeNode> stack = [];

  BSTIterator(TreeNode? root) {
    _pushAllLeft(root);
  }

  void _pushAllLeft(TreeNode? node) {
    while (node != null) {
      stack.add(node);
      node = node.left;
    }
  }

  int next() {
    TreeNode node = stack.removeLast();
    if (node.right != null) {
      _pushAllLeft(node.right);
    }
    return node.val;
  }

  bool hasNext() {
    return stack.isNotEmpty;
  }
}
```


### C#

```csharp
public class BSTIterator {
    private Stack<TreeNode> stack;

    public BSTIterator(TreeNode root) {
        stack = new Stack<TreeNode>();
        PushAllLeft(root);
    }

    private void PushAllLeft(TreeNode node) {
        while (node != null) {
            stack.Push(node);
            node = node.left;
        }
    }

    public int Next() {
        TreeNode node = stack.Pop();
        if (node.right != null) {
            PushAllLeft(node.right);
        }
        return node.val;
    }

    public bool HasNext() {
        return stack.Count > 0;
    }
}
```


### Java

```java
class BSTIterator {
    private Stack<TreeNode> stack;

    public BSTIterator(TreeNode root) {
        stack = new Stack<>();
        pushAllLeft(root);
    }

    private void pushAllLeft(TreeNode node) {
        while (node != null) {
            stack.push(node);
            node = node.left;
        }
    }

    public int next() {
        TreeNode node = stack.pop();
        if (node.right != null) {
            pushAllLeft(node.right);
        }
        return node.val;
    }

    public boolean hasNext() {
        return !stack.isEmpty();
    }
}
```


### Swift

```swift
class BSTIterator {
    private var stack: [TreeNode] = []

    init(_ root: TreeNode?) {
        pushAllLeft(root)
    }

    private func pushAllLeft(_ node: TreeNode?) {
        var current = node
        while current != nil {
            stack.append(current!)
            current = current?.left
        }
    }

    func next() -> Int {
        let node = stack.removeLast()
        if let right = node.right {
            pushAllLeft(right)
        }
        return node.val
    }

    func hasNext() -> Bool {
        return !stack.isEmpty
    }
}
```



### The End

