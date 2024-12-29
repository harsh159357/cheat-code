# House Robber III

## Problem Statement

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that all houses in this place form a binary tree. It will automatically contact the police if two directly-linked houses are broken into on the same night.

Determine the maximum amount of money the thief can rob without alerting the police.

## Input

```text
root = [3, 2, 3, null, 3, null, 1]
```

## Output

```text
7
```

## Input

```text
root = [3, 4, 5, 1, 3, null, 1]
```

## Output

```text
9
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
  Map<TreeNode, List<int>> memo = {};

  int rob(TreeNode? root) {
    if (root == null) return 0;
    if (memo.containsKey(root)) return memo[root]!.reduce((a, b) => a > b ? a : b);

    int rob = root.val +
        (root.left != null ? rob(root.left!.left) + rob(root.left!.right) : 0) +
        (root.right != null ? rob(root.right!.left) + rob(root.right!.right) : 0);

    int notRob = rob(root.left) + rob(root.right);

    memo[root] = [rob, notRob];
    return rob > notRob ? rob : notRob;
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
    public int Rob(TreeNode root) {
        var result = RobHelper(root);
        return Math.Max(result[0], result[1]);
    }

    private int[] RobHelper(TreeNode node) {
        if (node == null) return new int[2];

        int[] left = RobHelper(node.left);
        int[] right = RobHelper(node.right);

        int rob = node.val + left[1] + right[1];
        int notRob = Math.Max(left[0], left[1]) + Math.Max(right[0], right[1]);

        return new int[] { rob, notRob };
    }
}
```

### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
    }
}

class Solution {
    public int rob(TreeNode root) {
        int[] result = robSub(root);
        return Math.max(result[0], result[1]);
    }

    private int[] robSub(TreeNode node) {
        if (node == null) return new int[2];

        int[] left = robSub(node.left);
        int[] right = robSub(node.right);

        int rob = node.val + left[1] + right[1];
        int notRob = Math.max(left[0], left[1]) + Math.max(right[0], right[1]);

        return new int[] { rob, notRob };
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
    data class Robbery(val rob: Int, val notRob: Int)

    fun rob(root: TreeNode?): Int {
        val result = robSub(root)
        return maxOf(result.rob, result.notRob)
    }

    private fun robSub(root: TreeNode?): Robbery {
        if (root == null) return Robbery(0, 0)

        val left = robSub(root.left)
        val right = robSub(root.right)

        val rob = root.`val` + left.notRob + right.notRob
        val notRob = maxOf(left.rob, left.notRob) + maxOf(right.rob, right.notRob)

        return Robbery(rob, notRob)
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
    func rob(_ root: TreeNode?) -> Int {
        let result = robSub(root)
        return max(result.0, result.1)
    }

    private func robSub(_ root: TreeNode?) -> (Int, Int) {
        guard let root = root else { return (0, 0) }

        let left = robSub(root.left)
        let right = robSub(root.right)

        let rob = root.val + left.1 + right.1
        let notRob = max(left.0, left.1) + max(right.0, right.1)

        return (rob, notRob)
    }
}
```


### The End

