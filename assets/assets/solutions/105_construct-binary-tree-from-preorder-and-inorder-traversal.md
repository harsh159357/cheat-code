# Construct Binary Tree from Preorder and Inorder Traversal

## Problem Statement

Given two integer arrays `preorder` and `inorder` where:

- `preorder` is the preorder traversal of a binary tree.
- `inorder` is the inorder traversal of the same tree.

Construct and return the binary tree.

## Input

```text
preorder = [3, 9, 20, 15, 7]
inorder = [9, 3, 15, 20, 7]
```

## Output

```text
TreeNode representing the binary tree:
       3
      / \
     9   20
        /  \
       15   7
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

TreeNode? buildTree(List<int> preorder, List<int> inorder) {
  return buildTreeHelper(preorder, inorder, 0, 0, inorder.length - 1);
}

TreeNode? buildTreeHelper(List<int> preorder, List<int> inorder, int preStart, int inStart, int inEnd) {
  if (preStart > preorder.length - 1 || inStart > inEnd) return null;
  TreeNode root = TreeNode(preorder[preStart]);
  int inIndex = inStart;
  while (inorder[inIndex] != preorder[preStart]) inIndex++;
  root.left = buildTreeHelper(preorder, inorder, preStart + 1, inStart, inIndex - 1);
  root.right = buildTreeHelper(preorder, inorder, preStart + inIndex - inStart + 1, inIndex + 1, inEnd);
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
    public TreeNode BuildTree(int[] preorder, int[] inorder) {
        return BuildTreeHelper(preorder, inorder, 0, 0, inorder.Length - 1);
    }

    private TreeNode BuildTreeHelper(int[] preorder, int[] inorder, int preStart, int inStart, int inEnd) {
        if (preStart > preorder.Length - 1 || inStart > inEnd) return null;
        TreeNode root = new TreeNode(preorder[preStart]);
        int inIndex = inStart;
        while (inorder[inIndex] != preorder[preStart]) inIndex++;
        root.left = BuildTreeHelper(preorder, inorder, preStart + 1, inStart, inIndex - 1);
        root.right = BuildTreeHelper(preorder, inorder, preStart + inIndex - inStart + 1, inIndex + 1, inEnd);
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
    TreeNode() {}
    TreeNode(int val) { this.val = val; }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        return buildTreeHelper(preorder, inorder, 0, 0, inorder.length - 1);
    }

    private TreeNode buildTreeHelper(int[] preorder, int[] inorder, int preStart, int inStart, int inEnd) {
        if (preStart > preorder.length - 1 || inStart > inEnd) return null;
        TreeNode root = new TreeNode(preorder[preStart]);
        int inIndex = inStart;
        while (inorder[inIndex] != preorder[preStart]) inIndex++;
        root.left = buildTreeHelper(preorder, inorder, preStart + 1, inStart, inIndex - 1);
        root.right = buildTreeHelper(preorder, inorder, preStart + inIndex - inStart + 1, inIndex + 1, inEnd);
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
    fun buildTree(preorder: IntArray, inorder: IntArray): TreeNode? {
        return buildTreeHelper(preorder, inorder, 0, 0, inorder.size - 1)
    }

    private fun buildTreeHelper(preorder: IntArray, inorder: IntArray, preStart: Int, inStart: Int, inEnd: Int): TreeNode? {
        if (preStart > preorder.lastIndex || inStart > inEnd) return null
        val root = TreeNode(preorder[preStart])
        var inIndex = inStart
        while (inorder[inIndex] != preorder[preStart]) inIndex++
        root.left = buildTreeHelper(preorder, inorder, preStart + 1, inStart, inIndex - 1)
        root.right = buildTreeHelper(preorder, inorder, preStart + inIndex - inStart + 1, inIndex + 1, inEnd)
        return root
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
    func buildTree(_ preorder: [Int], _ inorder: [Int]) -> TreeNode? {
        return buildTreeHelper(preorder, inorder, 0, 0, inorder.count - 1)
    }

    private func buildTreeHelper(_ preorder: [Int], _ inorder: [Int], _ preStart: Int, _ inStart: Int, _ inEnd: Int) -> TreeNode? {
        if preStart > preorder.count - 1 || inStart > inEnd { return nil }
        let root = TreeNode(preorder[preStart])
        var inIndex = inStart
        while inorder[inIndex] != preorder[preStart] { inIndex += 1 }
        root.left = buildTreeHelper(preorder, inorder, preStart + 1, inStart, inIndex - 1)
        root.right = buildTreeHelper(preorder, inorder, preStart + inIndex - inStart + 1, inIndex + 1, inEnd)
        return root
    }
}
```

### The End

