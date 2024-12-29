# Binary Tree Maximum Path Sum

## Problem Statement

Given a non-empty binary tree, find the maximum path sum.  
A path in the binary tree is defined as any sequence of nodes starting and ending at any node in the tree.  
The path must go through parent-child connections, but it does not need to go through the root.

---

## Input

```text
root = [1,2,3]
```

## Output

```text
6
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

class Solution {
  int maxPathSum(TreeNode? root) {
    int maxSum = -1 << 31;
    int helper(TreeNode? node) {
      if (node == null) return 0;
      int leftSum = helper(node.left).clamp(0, double.infinity).toInt();
      int rightSum = helper(node.right).clamp(0, double.infinity).toInt();
      maxSum = max(maxSum, node.val + leftSum + rightSum);
      return node.val + max(leftSum, rightSum);
    }
    helper(root);
    return maxSum;
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
    public int MaxPathSum(TreeNode root) {
        int maxSum = int.MinValue;
        int Helper(TreeNode node) {
            if (node == null) return 0;
            int leftSum = Math.Max(Helper(node.left), 0);
            int rightSum = Math.Max(Helper(node.right), 0);
            maxSum = Math.Max(maxSum, node.val + leftSum + rightSum);
            return node.val + Math.Max(leftSum, rightSum);
        }
        Helper(root);
        return maxSum;
    }
}
```


### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {
    private int maxSum = Integer.MIN_VALUE;

    public int maxPathSum(TreeNode root) {
        maxPathSumHelper(root);
        return maxSum;
    }

    private int maxPathSumHelper(TreeNode node) {
        if (node == null) return 0;
        int leftSum = Math.max(maxPathSumHelper(node.left), 0);
        int rightSum = Math.max(maxPathSumHelper(node.right), 0);
        maxSum = Math.max(maxSum, node.val + leftSum + rightSum);
        return node.val + Math.max(leftSum, rightSum);
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
    fun maxPathSum(root: TreeNode?): Int {
        val maxSum = intArrayOf(Int.MIN_VALUE)
        maxPathSumHelper(root, maxSum)
        return maxSum[0]
    }

    private fun maxPathSumHelper(node: TreeNode?, maxSum: IntArray): Int {
        if (node == null) return 0
        val leftSum = maxOf(maxPathSumHelper(node.left, maxSum), 0)
        val rightSum = maxOf(maxPathSumHelper(node.right, maxSum), 0)
        maxSum[0] = maxOf(maxSum[0], node.`val` + leftSum + rightSum)
        return node.`val` + maxOf(leftSum, rightSum)
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
    func maxPathSum(_ root: TreeNode?) -> Int {
        var maxSum = Int.min
        func helper(_ node: TreeNode?) -> Int {
            guard let node = node else { return 0 }
            let leftSum = max(helper(node.left), 0)
            let rightSum = max(helper(node.right), 0)
            maxSum = max(maxSum, node.val + leftSum + rightSum)
            return node.val + max(leftSum, rightSum)
        }
        helper(root)
        return maxSum
    }
}
```


### The End

