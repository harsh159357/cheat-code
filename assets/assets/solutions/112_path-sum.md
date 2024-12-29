# Path Sum

## Problem Statement

Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a root-to-leaf path such that adding up all the values along the path equals `targetSum`.

A leaf is a node with no children.

## Input

```text
root = [5, 4, 8, 11, null, 13, 4, 7, 2, null, null, null, 1]
targetSum = 22
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

bool hasPathSum(TreeNode? root, int targetSum) {
  if (root == null) return false;
  if (root.left == null && root.right == null) return targetSum - root.val == 0;
  return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val);
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
    public bool HasPathSum(TreeNode root, int targetSum) {
        if (root == null) return false;
        if (root.left == null && root.right == null) return targetSum - root.val == 0;
        return HasPathSum(root.left, targetSum - root.val) || HasPathSum(root.right, targetSum - root.val);
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
    public boolean hasPathSum(TreeNode root, int targetSum) {
        if (root == null) return false;
        if (root.left == null && root.right == null) return targetSum - root.val == 0;
        return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val);
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
    fun hasPathSum(root: TreeNode?, targetSum: Int): Boolean {
        if (root == null) return false
        if (root.left == null && root.right == null && targetSum - root.`val` == 0) return true
        return hasPathSum(root.left, targetSum - root.`val`) || hasPathSum(root.right, targetSum - root.`val`)
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
    func hasPathSum(_ root: TreeNode?, _ targetSum: Int) -> Bool {
        guard let root = root else { return false }
        if root.left == nil && root.right == nil { return targetSum - root.val == 0 }
        return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val)
    }
}
```


### The End

