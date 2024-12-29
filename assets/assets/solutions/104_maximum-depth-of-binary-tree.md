# Maximum Depth of Binary Tree

## Problem Statement

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

## Input

```text
root = [3, 9, 20, null, null, 15, 7]
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

int maxDepth(TreeNode? root) {
  if (root == null) return 0;
  int leftDepth = maxDepth(root.left);
  int rightDepth = maxDepth(root.right);
  return 1 + (leftDepth > rightDepth ? leftDepth : rightDepth);
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
    public int MaxDepth(TreeNode root) {
        if (root == null) return 0;
        int leftDepth = MaxDepth(root.left);
        int rightDepth = MaxDepth(root.right);
        return 1 + Math.Max(leftDepth, rightDepth);
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
    public int maxDepth(TreeNode root) {
        if (root == null) return 0;
        int leftDepth = maxDepth(root.left);
        int rightDepth = maxDepth(root.right);
        return 1 + Math.max(leftDepth, rightDepth);
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
    fun maxDepth(root: TreeNode?): Int {
        if (root == null) return 0
        val leftDepth = maxDepth(root.left)
        val rightDepth = maxDepth(root.right)
        return 1 + maxOf(leftDepth, rightDepth)
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
    func maxDepth(_ root: TreeNode?) -> Int {
        guard let root = root else { return 0 }
        let leftDepth = maxDepth(root.left)
        let rightDepth = maxDepth(root.right)
        return 1 + max(leftDepth, rightDepth)
    }
}
```

### The End

