# Leaf-Similar Trees

## Problem Statement

Consider all the leaves of a binary tree, from left to right order, form a leaf value sequence. Two binary trees are considered leaf-similar if their leaf value sequence is the same.

Return `true` if and only if the two given trees are leaf-similar.

## Input

```text
root1 = [3, 5, 1, 6, 2, 9, 8, null, null, 7, 4]
root2 = [3, 5, 1, 6, 7, 4, 2, null, null, null, null, null, null, 9, 8]
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class TreeNode(var `val`: Int) {
    var left: TreeNode? = null
    var right: TreeNode? = null
}

class Solution {
    fun leafSimilar(root1: TreeNode?, root2: TreeNode?): Boolean {
        val leaves1 = mutableListOf<Int>()
        val leaves2 = mutableListOf<Int>()
        dfs(root1, leaves1)
        dfs(root2, leaves2)
        return leaves1 == leaves2
    }

    private fun dfs(node: TreeNode?, leaves: MutableList<Int>) {
        if (node == null) return
        if (node.left == null && node.right == null) {
            leaves.add(node.`val`)
        }
        dfs(node.left, leaves)
        dfs(node.right, leaves)
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

bool leafSimilar(TreeNode? root1, TreeNode? root2) {
  List<int> leaves1 = [];
  List<int> leaves2 = [];
  dfs(root1, leaves1);
  dfs(root2, leaves2);
  return leaves1.toString() == leaves2.toString();
}

void dfs(TreeNode? node, List<int> leaves) {
  if (node == null) return;
  if (node.left == null && node.right == null) {
    leaves.add(node.val);
  }
  dfs(node.left, leaves);
  dfs(node.right, leaves);
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
    public bool LeafSimilar(TreeNode root1, TreeNode root2) {
        var leaves1 = new List<int>();
        var leaves2 = new List<int>();
        Dfs(root1, leaves1);
        Dfs(root2, leaves2);
        return Enumerable.SequenceEqual(leaves1, leaves2);
    }

    private void Dfs(TreeNode node, List<int> leaves) {
        if (node == null) return;
        if (node.left == null && node.right == null) {
            leaves.Add(node.val);
        }
        Dfs(node.left, leaves);
        Dfs(node.right, leaves);
    }
}
```

### Java

```java
import java.util.*;

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int val) { this.val = val; }
}

class Solution {
    public boolean leafSimilar(TreeNode root1, TreeNode root2) {
        List<Integer> leaves1 = new ArrayList<>();
        List<Integer> leaves2 = new ArrayList<>();
        dfs(root1, leaves1);
        dfs(root2, leaves2);
        return leaves1.equals(leaves2);
    }

    private void dfs(TreeNode node, List<Integer> leaves) {
        if (node == null) return;
        if (node.left == null && node.right == null) {
            leaves.add(node.val);
        }
        dfs(node.left, leaves);
        dfs(node.right, leaves);
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
    func leafSimilar(_ root1: TreeNode?, _ root2: TreeNode?) -> Bool {
        var leaves1: [Int] = []
        var leaves2: [Int] = []
        dfs(root1, &leaves1)
        dfs(root2, &leaves2)
        return leaves1 == leaves2
    }

    private func dfs(_ node: TreeNode?, _ leaves: inout [Int]) {
        guard let node = node else { return }
        if node.left == nil && node.right == nil {
            leaves.append(node.val)
        }
        dfs(node.left, &leaves)
        dfs(node.right, &leaves)
    }
}
```

### The End