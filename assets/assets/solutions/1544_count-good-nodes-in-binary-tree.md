# Count Good Nodes in Binary Tree

## Problem Statement

A node in a binary tree is considered a **good node** if the path from the root to the node does not have any node with a value greater than the node's value. Given the root of a binary tree, return the number of good nodes in the tree.

## Input

```text
root = [3,1,4,3,null,1,5]
```

## Output

```text
4
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun goodNodes(root: TreeNode?): Int {
        return dfs(root, root?.`val` ?: Int.MIN_VALUE)
    }

    private fun dfs(node: TreeNode?, maxSoFar: Int): Int {
        if (node == null) return 0
        var count = 0
        if (node.`val` >= maxSoFar) {
            count++
        }
        count += dfs(node.left, maxOf(maxSoFar, node.`val`))
        count += dfs(node.right, maxOf(maxSoFar, node.`val`))
        return count
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

int goodNodes(TreeNode? root) {
  int dfs(TreeNode? node, int maxSoFar) {
    if (node == null) return 0;
    int count = 0;
    if (node.val >= maxSoFar) {
      count++;
    }
    count += dfs(node.left, node.val > maxSoFar ? node.val : maxSoFar);
    count += dfs(node.right, node.val > maxSoFar ? node.val : maxSoFar);
    return count;
  }

  return dfs(root, root?.val ?? -1 << 31);
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
    public int GoodNodes(TreeNode root) {
        return Dfs(root, int.MinValue);
    }

    private int Dfs(TreeNode node, int maxSoFar) {
        if (node == null) return 0;
        int count = 0;
        if (node.val >= maxSoFar) {
            count++;
        }
        count += Dfs(node.left, Math.Max(maxSoFar, node.val));
        count += Dfs(node.right, Math.Max(maxSoFar, node.val));
        return count;
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
    public int goodNodes(TreeNode root) {
        return dfs(root, Integer.MIN_VALUE);
    }

    private int dfs(TreeNode node, int maxSoFar) {
        if (node == null) return 0;
        int count = 0;
        if (node.val >= maxSoFar) {
            count++;
        }
        count += dfs(node.left, Math.max(maxSoFar, node.val));
        count += dfs(node.right, Math.max(maxSoFar, node.val));
        return count;
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
    func goodNodes(_ root: TreeNode?) -> Int {
        func dfs(_ node: TreeNode?, _ maxSoFar: Int) -> Int {
            guard let node = node else { return 0 }
            var count = 0
            if node.val >= maxSoFar {
                count += 1
            }
            count += dfs(node.left, max(maxSoFar, node.val))
            count += dfs(node.right, max(maxSoFar, node.val))
            return count
        }

        return dfs(root, root?.val ?? Int.min)
    }
}
```

### The End