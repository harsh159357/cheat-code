# Lowest Common Ancestor of a Binary Tree

## Problem Statement

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes `p` and `q`.

The LCA of two nodes `p` and `q` is defined as the lowest node in the tree that has both `p` and `q` as descendants.

## Input

```text
root = [3, 5, 1, 6, 2, 0, 8, null, null, 7, 4]
p = 5
q = 1
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

TreeNode? lowestCommonAncestor(TreeNode? root, TreeNode? p, TreeNode? q) {
  if (root == null || root == p || root == q) return root;

  TreeNode? left = lowestCommonAncestor(root.left, p, q);
  TreeNode? right = lowestCommonAncestor(root.right, p, q);

  return left != null && right != null ? root : left ?? right;
}
```

### C#

```csharp
public class TreeNode {
    public int val;
    public TreeNode left;
    public TreeNode right;
    public TreeNode(int x) { val = x; }
}

public class Solution {
    public TreeNode LowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null || root == p || root == q) return root;

        TreeNode left = LowestCommonAncestor(root.left, p, q);
        TreeNode right = LowestCommonAncestor(root.right, p, q);

        return left != null && right != null ? root : left ?? right;
    }
}
```

### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null || root == p || root == q) return root;

        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);

        return left != null && right != null ? root : left != null ? left : right;
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
    fun lowestCommonAncestor(root: TreeNode?, p: TreeNode?, q: TreeNode?): TreeNode? {
        if (root == null || root == p || root == q) return root

        val left = lowestCommonAncestor(root.left, p, q)
        val right = lowestCommonAncestor(root.right, p, q)

        return if (left != null && right != null) root else left ?: right
    }
}
```

### Swift

```swift
public class TreeNode {
    public var val: Int
    public var left: TreeNode?
    public var right: TreeNode?
    public init() { self.val = 0; self.left = nil; self.right = nil; }
    public init(_ val: Int) { self.val = val; self.left = nil; self.right = nil; }
    public init(_ val: Int, _ left: TreeNode?, _ right: TreeNode?) {
        self.val = val
        self.left = left
        self.right = right
    }
}

class Solution {
    func lowestCommonAncestor(_ root: TreeNode?, _ p: TreeNode?, _ q: TreeNode?) -> TreeNode? {
        if root == nil || root === p || root === q { return root }

        let left = lowestCommonAncestor(root?.left, p, q)
        let right = lowestCommonAncestor(root?.right, p, q)

        if left != nil && right != nil { return root }
        return left ?? right
    }
}
```

### The End

