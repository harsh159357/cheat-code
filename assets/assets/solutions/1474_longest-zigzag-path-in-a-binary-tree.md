# Longest ZigZag Path in a Binary Tree

## Problem Statement

Given the root of a binary tree, return the length of the longest ZigZag path in the tree.

A **ZigZag path** for a binary tree is defined as a sequence of nodes where each parent-child connection alternates between left and right. The length of a ZigZag path is the number of edges in the path.

## Input

```text
root = [1,null,2,3,null,4,5,null,6]
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun longestZigZag(root: TreeNode?): Int {
        if (root == null) return 0
        return maxOf(zigZag(root.left, false, 1), zigZag(root.right, true, 1))
    }

    private fun zigZag(node: TreeNode?, isRight: Boolean, count: Int): Int {
        if (node == null) return count - 1

        return if (isRight) {
            maxOf(zigZag(node.left, false, count + 1), zigZag(node.right, true, 1))
        } else {
            maxOf(zigZag(node.right, true, count + 1), zigZag(node.left, false, 1))
        }
    }
}
```

### Dart

```dart
class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;
  TreeNode(this.val, [this.left, this.right]);
}

int longestZigZag(TreeNode? root) {
  if (root == null) return 0;

  int zigZag(TreeNode? node, bool isRight, int count) {
    if (node == null) return count - 1;

    if (isRight) {
      return Math.max(zigZag(node.left, false, count + 1), zigZag(node.right, true, 1));
    } else {
      return Math.max(zigZag(node.right, true, count + 1), zigZag(node.left, false, 1));
    }
  }

  return Math.max(zigZag(root.left, false, 1), zigZag(root.right, true, 1));
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
    public int LongestZigZag(TreeNode root) {
        if (root == null) return 0;

        int ZigZag(TreeNode node, bool isRight, int count) {
            if (node == null) return count - 1;

            if (isRight) {
                return Math.Max(ZigZag(node.left, false, count + 1), ZigZag(node.right, true, 1));
            } else {
                return Math.Max(ZigZag(node.right, true, count + 1), ZigZag(node.left, false, 1));
            }
        }

        return Math.Max(ZigZag(root.left, false, 1), ZigZag(root.right, true, 1));
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
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    public int longestZigZag(TreeNode root) {
        if (root == null) return 0;

        return Math.max(zigZag(root.left, false, 1), zigZag(root.right, true, 1));
    }

    private int zigZag(TreeNode node, boolean isRight, int count) {
        if (node == null) return count - 1;

        if (isRight) {
            return Math.max(zigZag(node.left, false, count + 1), zigZag(node.right, true, 1));
        } else {
            return Math.max(zigZag(node.right, true, count + 1), zigZag(node.left, false, 1));
        }
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
    func longestZigZag(_ root: TreeNode?) -> Int {
        if root == nil { return 0 }

        func zigZag(_ node: TreeNode?, _ isRight: Bool, _ count: Int) -> Int {
            if node == nil { return count - 1 }

            if isRight {
                return max(zigZag(node?.left, false, count + 1), zigZag(node?.right, true, 1))
            } else {
                return max(zigZag(node?.right, true, count + 1), zigZag(node?.left, false, 1))
            }
        }

        return max(zigZag(root?.left, false, 1), zigZag(root?.right, true, 1))
    }
}
```

### The End