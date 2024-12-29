# Flatten Binary Tree to Linked List

## Problem Statement

Given the `root` of a binary tree, flatten the tree into a "linked list":

- The "linked list" should use the same `TreeNode` class where the `right` child pointer points to the next node in the list and the `left` child pointer is always `null`.
- The "linked list" should be in the same order as a pre-order traversal of the binary tree.

## Input

```text
root = [1, 2, 5, 3, 4, null, 6]
```

## Output

```text
[1, null, 2, null, 3, null, 4, null, 5, null, 6]
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

void flatten(TreeNode? root) {
  TreeNode? current = root;
  while (current != null) {
    if (current.left != null) {
      TreeNode? mostRight = current.left;
      while (mostRight?.right != null) {
        mostRight = mostRight?.right;
      }
      mostRight?.right = current.right;
      current.right = current.left;
      current.left = null;
    }
    current = current.right;
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
    public void Flatten(TreeNode root) {
        TreeNode current = root;
        while (current != null) {
            if (current.left != null) {
                TreeNode mostRight = current.left;
                while (mostRight.right != null) {
                    mostRight = mostRight.right;
                }
                mostRight.right = current.right;
                current.right = current.left;
                current.left = null;
            }
            current = current.right;
        }
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
    public void flatten(TreeNode root) {
        TreeNode current = root;
        while (current != null) {
            if (current.left != null) {
                TreeNode mostRight = current.left;
                while (mostRight.right != null) {
                    mostRight = mostRight.right;
                }
                mostRight.right = current.right;
                current.right = current.left;
                current.left = null;
            }
            current = current.right;
        }
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
    fun flatten(root: TreeNode?) {
        var current = root
        while (current != null) {
            if (current.left != null) {
                var mostRight = current.left
                while (mostRight?.right != null) mostRight = mostRight.right
                mostRight?.right = current.right
                current.right = current.left
                current.left = null
            }
            current = current.right
        }
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
    func flatten(_ root: TreeNode?) {
        var current = root
        while current != nil {
            if let left = current?.left {
                var mostRight = left
                while mostRight.right != nil {
                    mostRight = mostRight.right!
                }
                mostRight.right = current?.right
                current?.right = left
                current?.left = nil
            }
            current = current?.right
        }
    }
}
```

### The End

