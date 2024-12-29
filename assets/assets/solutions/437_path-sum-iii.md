# Path Sum III

## Problem Statement

Given the `root` of a binary tree and an integer `targetSum`, return the number of paths where the sum of the values along the path equals `targetSum`.

The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).

## Input

```text
root = [10,5,-3,3,2,null,11,3,-2,null,1]
targetSum = 8
```

## Output

```text
3
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

int pathSum(TreeNode? root, int targetSum) {
  if (root == null) return 0;

  int pathSumFromNode(TreeNode? node, int target) {
    if (node == null) return 0;

    int count = 0;
    if (target == node.val) count++;

    count += pathSumFromNode(node.left, target - node.val);
    count += pathSumFromNode(node.right, target - node.val);

    return count;
  }

  return pathSumFromNode(root, targetSum) +
      pathSum(root.left, targetSum) +
      pathSum(root.right, targetSum);
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
    public int PathSum(TreeNode root, int targetSum) {
        if (root == null) return 0;

        int PathSumFromNode(TreeNode node, long target) {
            if (node == null) return 0;

            int count = 0;
            if (target == node.val) count++;

            count += PathSumFromNode(node.left, target - node.val);
            count += PathSumFromNode(node.right, target - node.val);

            return count;
        }

        return PathSumFromNode(root, targetSum) +
               PathSum(root.left, targetSum) +
               PathSum(root.right, targetSum);
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
    public int pathSum(TreeNode root, int targetSum) {
        if (root == null) return 0;

        int pathSumFromNode(TreeNode node, long target) {
            if (node == null) return 0;

            int count = 0;
            if (target == node.val) count++;

            count += pathSumFromNode(node.left, target - node.val);
            count += pathSumFromNode(node.right, target - node.val);

            return count;
        }

        return pathSumFromNode(root, targetSum) +
               pathSum(root.left, targetSum) +
               pathSum(root.right, targetSum);
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
    fun pathSum(root: TreeNode?, targetSum: Int): Int {
        if (root == null) return 0

        fun pathSumNode(root: TreeNode?, targetSum: Long): Int {
            if (root == null) return 0

            var count = 0
            if (targetSum - root.`val` == 0L) count++

            count += pathSumNode(root.left, targetSum - root.`val`)
            count += pathSumNode(root.right, targetSum - root.`val`)

            return count
        }

        return pathSumNode(root, targetSum.toLong()) +
                pathSum(root.left, targetSum) +
                pathSum(root.right, targetSum)
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
    func pathSum(_ root: TreeNode?, _ targetSum: Int) -> Int {
        guard let root = root else { return 0 }

        func pathSumFromNode(_ node: TreeNode?, _ target: Int) -> Int {
            guard let node = node else { return 0 }

            var count = 0
            if target == node.val { count += 1 }

            count += pathSumFromNode(node.left, target - node.val)
            count += pathSumFromNode(node.right, target - node.val)

            return count
        }

        return pathSumFromNode(root, targetSum) +
               pathSum(root.left, targetSum) +
               pathSum(root.right, targetSum)
    }
}
```

### The End