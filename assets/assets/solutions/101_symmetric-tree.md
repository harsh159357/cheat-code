# Symmetric Tree

## Problem Statement

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

## Input

```text
root = [1, 2, 2, 3, 4, 4, 3]
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

bool isSymmetric(TreeNode? root) {
  if (root == null) return true;
  return isMirror(root.left, root.right);
}

bool isMirror(TreeNode? left, TreeNode? right) {
  if (left == null && right == null) return true;
  if (left == null || right == null) return false;
  return (left.val == right.val) && 
         isMirror(left.left, right.right) && 
         isMirror(left.right, right.left);
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
    public bool IsSymmetric(TreeNode root) {
        return root == null || IsMirror(root.left, root.right);
    }

    private bool IsMirror(TreeNode left, TreeNode right) {
        if (left == null && right == null) return true;
        if (left == null || right == null) return false;
        return (left.val == right.val) && IsMirror(left.left, right.right) && IsMirror(left.right, right.left);
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
    public boolean isSymmetric(TreeNode root) {
        return root == null || isMirror(root.left, root.right);
    }

    private boolean isMirror(TreeNode left, TreeNode right) {
        if (left == null && right == null) return true;
        if (left == null || right == null) return false;
        return (left.val == right.val) && isMirror(left.left, right.right) && isMirror(left.right, right.left);
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
    fun isSymmetric(root: TreeNode?): Boolean {
        return root == null || isMirror(root.left, root.right)
    }

    private fun isMirror(left: TreeNode?, right: TreeNode?): Boolean {
        if (left == null && right == null) return true
        if (left == null || right == null) return false
        return (left.`val` == right.`val`) &&
                isMirror(left.left, right.right) &&
                isMirror(left.right, right.left)
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
    func isSymmetric(_ root: TreeNode?) -> Bool {
        return root == nil || isMirror(root?.left, root?.right)
    }

    private func isMirror(_ left: TreeNode?, _ right: TreeNode?) -> Bool {
        if left == nil && right == nil { return true }
        if left == nil || right == nil { return false }
        return (left!.val == right!.val) &&
               isMirror(left!.left, right!.right) &&
               isMirror(left!.right, right!.left)
    }
}
```

### The End

