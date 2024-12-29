# Construct Binary Tree from Inorder and Postorder Traversal

## Problem Statement

Given two integer arrays `inorder` and `postorder` where:

- `inorder` is the inorder traversal of a binary tree.
- `postorder` is the postorder traversal of the same tree.

Construct and return the binary tree.

## Input

```text
inorder = [9, 3, 15, 20, 7]
postorder = [9, 15, 7, 20, 3]
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

TreeNode? buildTree(List<int> inorder, List<int> postorder) {
  return buildTreeHelper(inorder, postorder, 0, inorder.length - 1, postorder.length - 1);
}

TreeNode? buildTreeHelper(List<int> inorder, List<int> postorder, int inStart, int inEnd, int postEnd) {
  if (inStart > inEnd || postEnd < 0) return null;
  TreeNode root = TreeNode(postorder[postEnd]);
  int inIndex = inStart;
  while (inorder[inIndex] != postorder[postEnd]) inIndex++;
  root.right = buildTreeHelper(inorder, postorder, inIndex + 1, inEnd, postEnd - 1);
  root.left = buildTreeHelper(inorder, postorder, inStart, inIndex - 1, postEnd - (inEnd - inIndex) - 1);
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
    public TreeNode BuildTree(int[] inorder, int[] postorder) {
        return BuildTreeHelper(inorder, postorder, 0, inorder.Length - 1, postorder.Length - 1);
    }

    private TreeNode BuildTreeHelper(int[] inorder, int[] postorder, int inStart, int inEnd, int postEnd) {
        if (inStart > inEnd || postEnd < 0) return null;
        TreeNode root = new TreeNode(postorder[postEnd]);
        int inIndex = inStart;
        while (inorder[inIndex] != postorder[postEnd]) inIndex++;
        root.right = BuildTreeHelper(inorder, postorder, inIndex + 1, inEnd, postEnd - 1);
        root.left = BuildTreeHelper(inorder, postorder, inStart, inIndex - 1, postEnd - (inEnd - inIndex) - 1);
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
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        return buildTreeHelper(inorder, postorder, 0, inorder.length - 1, postorder.length - 1);
    }

    private TreeNode buildTreeHelper(int[] inorder, int[] postorder, int inStart, int inEnd, int postEnd) {
        if (inStart > inEnd || postEnd < 0) return null;
        TreeNode root = new TreeNode(postorder[postEnd]);
        int inIndex = inStart;
        while (inorder[inIndex] != postorder[postEnd]) inIndex++;
        root.right = buildTreeHelper(inorder, postorder, inIndex + 1, inEnd, postEnd - 1);
        root.left = buildTreeHelper(inorder, postorder, inStart, inIndex - 1, postEnd - (inEnd - inIndex) - 1);
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
    fun buildTree(inorder: IntArray, postorder: IntArray): TreeNode? {
        return buildTreeHelper(inorder, postorder, 0, inorder.size - 1, postorder.size - 1)
    }

    private fun buildTreeHelper(inorder: IntArray, postorder: IntArray, inStart: Int, inEnd: Int, postEnd: Int): TreeNode? {
        if (inStart > inEnd || postEnd < 0) return null
        val root = TreeNode(postorder[postEnd])
        var inIndex = inStart
        while (inorder[inIndex] != postorder[postEnd]) inIndex++
        root.right = buildTreeHelper(inorder, postorder, inIndex + 1, inEnd, postEnd - 1)
        root.left = buildTreeHelper(inorder, postorder, inStart, inIndex - 1, postEnd - (inEnd - inIndex) - 1)
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
    func buildTree(_ inorder: [Int], _ postorder: [Int]) -> TreeNode? {
        return buildTreeHelper(inorder, postorder, 0, inorder.count - 1, postorder.count - 1)
    }

    private func buildTreeHelper(_ inorder: [Int], _ postorder: [Int], _ inStart: Int, _ inEnd: Int, _ postEnd: Int) -> TreeNode? {
        if inStart > inEnd || postEnd < 0 { return nil }
        let root = TreeNode(postorder[postEnd])
        var inIndex = inStart
        while inorder[inIndex] != postorder[postEnd] { inIndex += 1 }
        root.right = buildTreeHelper(inorder, postorder, inIndex + 1, inEnd, postEnd - 1)
        root.left = buildTreeHelper(inorder, postorder, inStart, inIndex - 1, postEnd - (inEnd - inIndex) - 1)
        return root
    }
}
```

### The End
