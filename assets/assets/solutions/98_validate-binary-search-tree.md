# Validate Binary Search Tree

## Problem Statement

Given the `root` of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:
- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

## Input

```text
root = [2, 1, 3]
```

## Output

```text
true
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

bool isValidBST(TreeNode? root) {
  bool validate(TreeNode? node, int? min, int? max) {
    if (node == null) return true;
    if ((min != null && node.val <= min) || (max != null && node.val >= max)) return false;
    return validate(node.left, min, node.val) && validate(node.right, node.val, max);
  }

  return validate(root, null, null);
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
    public bool IsValidBST(TreeNode root) {
        return Validate(root, null, null);
    }

    private bool Validate(TreeNode node, int? min, int? max) {
        if (node == null) return true;
        if ((min != null && node.val <= min) || (max != null && node.val >= max)) return false;
        return Validate(node.left, min, node.val) && Validate(node.right, node.val, max);
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
    public boolean isValidBST(TreeNode root) {
        return validate(root, null, null);
    }

    private boolean validate(TreeNode node, Integer min, Integer max) {
        if (node == null) return true;
        if ((min != null && node.val <= min) || (max != null && node.val >= max)) return false;
        return validate(node.left, min, node.val) && validate(node.right, node.val, max);
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
    fun isValidBST(root: TreeNode?): Boolean {
        fun isValid(node: TreeNode?, min: Int?, max: Int?): Boolean {
            if (node == null) return true
            if ((min != null && node.`val` <= min) || (max != null && node.`val` >= max)) return false
            return isValid(node.left, min, node.`val`) && isValid(node.right, node.`val`, max)
        }

        return isValid(root, null, null)
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
    func isValidBST(_ root: TreeNode?) -> Bool {
        func validate(_ node: TreeNode?, _ min: Int?, _ max: Int?) -> Bool {
            guard let node = node else { return true }
            if let min = min, node.val <= min { return false }
            if let max = max, node.val >= max { return false }
            return validate(node.left, min, node.val) && validate(node.right, node.val, max)
        }

        return validate(root, nil, nil)
    }
}
```

### The End

