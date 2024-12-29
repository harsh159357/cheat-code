# Diameter of Binary Tree

## Problem Statement

Given the `root` of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

## Input

```text
root = [1, 2, 3, 4, 5]
```

## Output

```text
3
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

class Solution {
  int ans = 0;

  int diameterOfBinaryTree(TreeNode? root) {
    ans = 1;
    depth(root);
    return ans - 1;
  }

  int depth(TreeNode? node) {
    if (node == null) return 0;
    int leftDepth = depth(node.left);
    int rightDepth = depth(node.right);
    ans = (ans > leftDepth + rightDepth + 1) ? ans : leftDepth + rightDepth + 1;
    return (leftDepth > rightDepth ? leftDepth : rightDepth) + 1;
  }
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
    private int ans = 0;

    public int DiameterOfBinaryTree(TreeNode root) {
        ans = 1;
        Depth(root);
        return ans - 1;
    }

    private int Depth(TreeNode node) {
        if (node == null) return 0;
        int leftDepth = Depth(node.left);
        int rightDepth = Depth(node.right);
        ans = Math.Max(ans, leftDepth + rightDepth + 1);
        return Math.Max(leftDepth, rightDepth) + 1;
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
    private int ans = 0;

    public int diameterOfBinaryTree(TreeNode root) {
        ans = 1;
        depth(root);
        return ans - 1;
    }

    private int depth(TreeNode node) {
        if (node == null) return 0;
        int leftDepth = depth(node.left);
        int rightDepth = depth(node.right);
        ans = Math.max(ans, leftDepth + rightDepth + 1);
        return Math.max(leftDepth, rightDepth) + 1;
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
    private var ans = 0

    fun diameterOfBinaryTree(root: TreeNode?): Int {
        ans = 1
        depth(root)
        return ans - 1
    }

    private fun depth(node: TreeNode?): Int {
        if (node == null) return 0
        val leftDepth = depth(node.left)
        val rightDepth = depth(node.right)
        ans = maxOf(ans, leftDepth + rightDepth + 1)
        return maxOf(leftDepth, rightDepth) + 1
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
        self.left = left;
        self.right = right;
    }
}

class Solution {
    private var ans = 0

    func diameterOfBinaryTree(_ root: TreeNode?) -> Int {
        ans = 1
        _ = depth(root)
        return ans - 1
    }

    private func depth(_ node: TreeNode?) -> Int {
        guard let node = node else { return 0 }
        let leftDepth = depth(node.left)
        let rightDepth = depth(node.right)
        ans = max(ans, leftDepth + rightDepth + 1)
        return max(leftDepth, rightDepth) + 1
    }
}
```

### The End