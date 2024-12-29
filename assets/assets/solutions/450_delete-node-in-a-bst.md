# Delete Node in a BST

## Problem Statement

Given a root node of a Binary Search Tree (BST) and a key, delete the node with the given key and return the root node of the updated BST. The deletion process must maintain the properties of a BST.

### Rules for Deletion:

1. If the node to be deleted has no children, simply remove it.
2. If the node to be deleted has one child, replace the node with its child.
3. If the node to be deleted has two children:
    - Replace the node's value with the smallest value in its right subtree.
    - Delete that smallest value node from the right subtree.

## Input

```text
root = [5,3,6,2,4,null,7], key = 3
```

## Output

```text
[5,4,6,2,null,null,7]
```

## Solutions

### Dart

```dart
class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;
  TreeNode(this.val, [this.left, this.right]);
}

TreeNode? deleteNode(TreeNode? root, int key) {
  if (root == null) return null;

  if (key < root.val) {
    root.left = deleteNode(root.left, key);
  } else if (key > root.val) {
    root.right = deleteNode(root.right, key);
  } else {
    if (root.left == null) return root.right;
    if (root.right == null) return root.left;

    TreeNode? minNode = root.right;
    while (minNode?.left != null) {
      minNode = minNode?.left;
    }
    root.val = minNode!.val;
    root.right = deleteNode(root.right, root.val);
  }

  return root;
}
```

### C#

```csharp
public class TreeNode {
    public int val;
    public TreeNode left;
    public TreeNode right;
    public TreeNode(int val = 0, TreeNode left = null, TreeNode right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

public class Solution {
    public TreeNode DeleteNode(TreeNode root, int key) {
        if (root == null) return null;

        if (key < root.val) {
            root.left = DeleteNode(root.left, key);
        } else if (key > root.val) {
            root.right = DeleteNode(root.right, key);
        } else {
            if (root.left == null) return root.right;
            if (root.right == null) return root.left;

            TreeNode minNode = GetMin(root.right);
            root.val = minNode.val;
            root.right = DeleteNode(root.right, root.val);
        }

        return root;
    }

    private TreeNode GetMin(TreeNode node) {
        while (node.left != null) node = node.left;
        return node;
    }
}
```

### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode() {}
    TreeNode(int val) { this.val = val; }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        if (root == null) return null;

        if (key < root.val) {
            root.left = deleteNode(root.left, key);
        } else if (key > root.val) {
            root.right = deleteNode(root.right, key);
        } else {
            if (root.left == null) return root.right;
            if (root.right == null) return root.left;

            TreeNode minNode = getMin(root.right);
            root.val = minNode.val;
            root.right = deleteNode(root.right, root.val);
        }

        return root;
    }

    private TreeNode getMin(TreeNode node) {
        while (node.left != null) node = node.left;
        return node;
    }
}
```

### Kotlin

```kotlin
class TreeNode(var `val`: Int) {
    var left: TreeNode? = null
    var right: TreeNode? = null
}

class Solution {
    fun deleteNode(root: TreeNode?, key: Int): TreeNode? {
        if (root == null) return null

        if (key < root.`val`) {
            root.left = deleteNode(root.left, key)
        } else if (key > root.`val`) {
            root.right = deleteNode(root.right, key)
        } else {
            if (root.left == null) return root.right
            if (root.right == null) return root.left

            var minNode = root.right
            while (minNode?.left != null) {
                minNode = minNode.left
            }
            root.`val` = minNode!!.`val`
            root.right = deleteNode(root.right, root.`val`)
        }

        return root
    }
}
```

### Swift

```swift
class TreeNode {
    var val: Int
    var left: TreeNode?
    var right: TreeNode?
    init(_ val: Int) {
        self.val = val
        self.left = nil
        self.right = nil
    }
}

class Solution {
    func deleteNode(_ root: TreeNode?, _ key: Int) -> TreeNode? {
        guard let root = root else { return nil }

        if key < root.val {
            root.left = deleteNode(root.left, key)
        } else if key > root.val {
            root.right = deleteNode(root.right, key)
        } else {
            if root.left == nil { return root.right }
            if root.right == nil { return root.left }

            let minNode = getMin(root.right!)
            root.val = minNode.val
            root.right = deleteNode(root.right, root.val)
        }

        return root
    }

    private func getMin(_ node: TreeNode) -> TreeNode {
        var current = node
        while let left = current.left {
            current = left
        }
        return current
    }
}
```

### The End