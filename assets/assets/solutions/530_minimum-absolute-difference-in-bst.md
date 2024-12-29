# Minimum Absolute Difference in BST

## Problem Statement

Given the root of a Binary Search Tree (BST), return the minimum absolute difference between the values of any two nodes in the BST.

### Properties of a BST

1. The left subtree of a node contains only nodes with keys less than the node's key.
2. The right subtree of a node contains only nodes with keys greater than the node's key.

## Input

```text
root = [4, 2, 6, 1, 3]
```

## Output

```text
1
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

int getMinimumDifference(TreeNode? root) {
  int minDiff = double.maxFinite.toInt();
  int? prev = null;

  void inOrder(TreeNode? node) {
    if (node == null) return;

    inOrder(node.left);

    if (prev != null) {
      minDiff = (node.val - prev!).min(minDiff);
    }
    prev = node.val;

    inOrder(node.right);
  }

  inOrder(root);
  return minDiff;
}

extension Min on int {
  int min(int other) => this < other ? this : other;
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
    private int minDiff = int.MaxValue;
    private int? prev = null;

    public int GetMinimumDifference(TreeNode root) {
        InOrder(root);
        return minDiff;
    }

    private void InOrder(TreeNode node) {
        if (node == null) return;

        InOrder(node.left);

        if (prev.HasValue) {
            minDiff = Math.Min(minDiff, node.val - prev.Value);
        }
        prev = node.val;

        InOrder(node.right);
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
    private int minDiff = Integer.MAX_VALUE;
    private Integer prev = null;

    public int getMinimumDifference(TreeNode root) {
        inOrder(root);
        return minDiff;
    }

    private void inOrder(TreeNode node) {
        if (node == null) return;

        inOrder(node.left);

        if (prev != null) {
            minDiff = Math.min(minDiff, node.val - prev);
        }
        prev = node.val;

        inOrder(node.right);
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
    private var minDiff = Int.MAX_VALUE
    private var prev: Int? = null

    private fun inOrderTraversal(node: TreeNode?) {
        if (node == null) return

        inOrderTraversal(node.left)

        if (prev != null) {
            minDiff = minOf(minDiff, node.`val` - prev!!)
        }
        prev = node.`val`

        inOrderTraversal(node.right)
    }

    fun getMinimumDifference(root: TreeNode?): Int {
        inOrderTraversal(root)
        return minDiff
    }
}
```

### Swift

```swift
class TreeNode {
    var val: Int
    var left: TreeNode?
    var right: TreeNode?
    init(_ val: Int) { self.val = val; self.left = nil; self.right = nil }
}

class Solution {
    private var minDiff = Int.max
    private var prev: Int?

    func getMinimumDifference(_ root: TreeNode?) -> Int {
        inOrder(root)
        return minDiff
    }

    private func inOrder(_ node: TreeNode?) {
        guard let node = node else { return }

        inOrder(node.left)

        if let prev = prev {
            minDiff = min(minDiff, node.val - prev)
        }
        prev = node.val

        inOrder(node.right)
    }
}
```

### The End