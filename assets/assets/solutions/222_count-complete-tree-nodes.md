# Count Complete Tree Nodes

## Problem Statement

Given the `root` of a complete binary tree, return the number of the nodes in the tree.

A complete binary tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible.

## Input

```text
root = [1, 2, 3, 4, 5, 6]
```

## Output

```text
6
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

int countNodes(TreeNode? root) {
  if (root == null) return 0;
  int leftHeight = _leftHeight(root);
  int rightHeight = _rightHeight(root);
  return leftHeight == rightHeight
      ? (1 << leftHeight) - 1
      : 1 + countNodes(root.left) + countNodes(root.right);
}

int _leftHeight(TreeNode? root) {
  int height = 0;
  while (root != null) {
    height++;
    root = root.left;
  }
  return height;
}

int _rightHeight(TreeNode? root) {
  int height = 0;
  while (root != null) {
    height++;
    root = root.right;
  }
  return height;
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
    public int CountNodes(TreeNode root) {
        if (root == null) return 0;
        int leftHeight = LeftHeight(root);
        int rightHeight = RightHeight(root);
        return leftHeight == rightHeight 
            ? (1 << leftHeight) - 1 
            : 1 + CountNodes(root.left) + CountNodes(root.right);
    }

    private int LeftHeight(TreeNode root) {
        int height = 0;
        while (root != null) {
            height++;
            root = root.left;
        }
        return height;
    }

    private int RightHeight(TreeNode root) {
        int height = 0;
        while (root != null) {
            height++;
            root = root.right;
        }
        return height;
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
    public int countNodes(TreeNode root) {
        if (root == null) return 0;
        int leftHeight = leftHeight(root);
        int rightHeight = rightHeight(root);
        return leftHeight == rightHeight 
            ? (1 << leftHeight) - 1 
            : 1 + countNodes(root.left) + countNodes(root.right);
    }

    private int leftHeight(TreeNode root) {
        int height = 0;
        while (root != null) {
            height++;
            root = root.left;
        }
        return height;
    }

    private int rightHeight(TreeNode root) {
        int height = 0;
        while (root != null) {
            height++;
            root = root.right;
        }
        return height;
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
    fun countNodes(root: TreeNode?): Int {
        if (root == null) return 0
        val leftHeight = leftHeight(root)
        val rightHeight = rightHeight(root)
        return if (leftHeight == rightHeight) 
            (1 shl leftHeight) - 1 
        else 
            1 + countNodes(root.left) + countNodes(root.right)
    }

    private fun leftHeight(root: TreeNode?): Int {
        var node = root
        var height = 0
        while (node != null) {
            height++
            node = node.left
        }
        return height
    }

    private fun rightHeight(root: TreeNode?): Int {
        var node = root
        var height = 0
        while (node != null) {
            height++
            node = node.right
        }
        return height
    }
}
```

### Swift

```swift
class TreeNode {
    var val: Int
    var left: TreeNode?
    var right: TreeNode?
    init(_ val: Int, _ left: TreeNode? = nil, _ right: TreeNode? = nil) {
        self.val = val
        self.left = left
        self.right = right
    }
}

class Solution {
    func countNodes(_ root: TreeNode?) -> Int {
        guard let root = root else { return 0 }
        let leftHeight = leftHeight(root)
        let rightHeight = rightHeight(root)
        return leftHeight == rightHeight 
            ? (1 << leftHeight) - 1 
            : 1 + countNodes(root.left) + countNodes(root.right)
    }

    private func leftHeight(_ root: TreeNode?) -> Int {
        var node = root
        var height = 0
        while node != nil {
            height += 1
            node = node?.left
        }
        return height
    }

    private func rightHeight(_ root: TreeNode?) -> Int {
        var node = root
        var height = 0
        while node != nil {
            height += 1
            node = node?.right
        }
        return height
    }
}
```


### The End

