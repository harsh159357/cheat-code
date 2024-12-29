# Binary Tree Inorder Traversal

## Problem Statement

Given the `root` of a binary tree, return the inorder traversal of its nodes' values.

## Input

```text
root = [1,null,2,3]
```

## Output

```text
[1,3,2]
```

(Explanation: The inorder traversal visits nodes in the order: left subtree, root, right subtree.)

## Solutions

### Dart

```dart
class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;
  TreeNode(this.val, [this.left, this.right]);
}

List<int> inorderTraversal(TreeNode? root) {
  List<int> result = [];
  void inorder(TreeNode? node) {
    if (node == null) return;
    inorder(node.left);
    result.add(node.val);
    inorder(node.right);
  }
  inorder(root);
  return result;
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
    public IList<int> InorderTraversal(TreeNode root) {
        var result = new List<int>();
        void Inorder(TreeNode node) {
            if (node == null) return;
            Inorder(node.left);
            result.Add(node.val);
            Inorder(node.right);
        }
        Inorder(root);
        return result;
    }
}
```

### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int val) { this.val = val; this.left = null; this.right = null; }
}

class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        inorder(root, result);
        return result;
    }

    private void inorder(TreeNode node, List<Integer> result) {
        if (node == null) return;
        inorder(node.left, result);
        result.add(node.val);
        inorder(node.right, result);
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
    fun inorderTraversal(root: TreeNode?): List<Int> {
        val result = mutableListOf<Int>()
        fun inorder(node: TreeNode?) {
            if (node == null) return
            inorder(node.left)
            result.add(node.`val`)
            inorder(node.right)
        }
        inorder(root)
        return result
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
    func inorderTraversal(_ root: TreeNode?) -> [Int] {
        var result = [Int]()
        func inorder(_ node: TreeNode?) {
            guard let node = node else { return }
            inorder(node.left)
            result.append(node.val)
            inorder(node.right)
        }
        inorder(root)
        return result
    }
}
```

### The End

