# Invert Binary Tree

## Problem Statement

Given the root of a binary tree, invert the tree and return its root.

## Input

```text
Input: root = [4,2,7,1,3,6,9]
```

## Output

```text
Output: [4,7,2,9,6,3,1]
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

TreeNode? invertTree(TreeNode? root) {
  if (root == null) return null;
  TreeNode? left = invertTree(root.right);
  TreeNode? right = invertTree(root.left);
  root.left = left;
  root.right = right;
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
    public TreeNode InvertTree(TreeNode root) {
        if (root == null) return null;
        TreeNode left = InvertTree(root.right);
        TreeNode right = InvertTree(root.left);
        root.left = left;
        root.right = right;
        return root;
    }
}
```

### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int val) { this.val = val; }
}

class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) return null;
        TreeNode left = invertTree(root.right);
        TreeNode right = invertTree(root.left);
        root.left = left;
        root.right = right;
        return root;
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
    fun invertTree(root: TreeNode?): TreeNode? {
        if (root == null) return null
        val left = invertTree(root.right)
        val right = invertTree(root.left)
        root.left = left
        root.right = right
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
    init(_ val: Int, _ left: TreeNode? = nil, _ right: TreeNode? = nil) {
        self.val = val
        self.left = left
        self.right = right
    }
}

class Solution {
    func invertTree(_ root: TreeNode?) -> TreeNode? {
        guard let root = root else { return nil }
        let left = invertTree(root.right)
        let right = invertTree(root.left)
        root.left = left
        root.right = right
        return root
    }
}
```


### The End

