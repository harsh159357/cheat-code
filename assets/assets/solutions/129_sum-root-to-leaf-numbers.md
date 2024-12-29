# Sum Root to Leaf Numbers

## Problem Statement

You are given the `root` of a binary tree containing digits from `0-9` only. Each root-to-leaf path in the tree represents a number.

For example, the root-to-leaf path `1 -> 2 -> 3` represents the number `123`.

Return the total sum of all root-to-leaf numbers. The test cases are generated so that the answer will fit in a 32-bit integer.

A leaf node is a node with no children.

---

## Input

```text
root = [1,2,3]
```

## Output

```text
25
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

int sumNumbers(TreeNode? root) {
  return sumNumbersHelper(root, 0);
}

int sumNumbersHelper(TreeNode? root, int sum) {
  if (root == null) return 0;
  int currentSum = sum * 10 + root.val;
  if (root.left == null && root.right == null) return currentSum;
  return sumNumbersHelper(root.left, currentSum) + sumNumbersHelper(root.right, currentSum);
}
```


### C#

```csharp
public class TreeNode {
    public int val;
    public TreeNode left;
    public TreeNode right;
    public TreeNode(int val=0, TreeNode left=null, TreeNode right=null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

public class Solution {
    public int SumNumbers(TreeNode root) {
        return SumNumbersHelper(root, 0);
    }

    private int SumNumbersHelper(TreeNode root, int sum) {
        if (root == null) return 0;
        int currentSum = sum * 10 + root.val;
        if (root.left == null && root.right == null) return currentSum;
        return SumNumbersHelper(root.left, currentSum) + SumNumbersHelper(root.right, currentSum);
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
    public int sumNumbers(TreeNode root) {
        return sumNumbersHelper(root, 0);
    }

    private int sumNumbersHelper(TreeNode root, int sum) {
        if (root == null) return 0;
        int currentSum = sum * 10 + root.val;
        if (root.left == null && root.right == null) return currentSum;
        return sumNumbersHelper(root.left, currentSum) + sumNumbersHelper(root.right, currentSum);
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
    fun sumNumbers(root: TreeNode?): Int {
        return sumNumbersHelper(root, 0)
    }

    private fun sumNumbersHelper(root: TreeNode?, sum: Int): Int {
        if (root == null) return 0
        val currentSum = sum * 10 + root.`val`
        if (root.left == null && root.right == null) return currentSum
        return sumNumbersHelper(root.left, currentSum) + sumNumbersHelper(root.right, currentSum)
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
    func sumNumbers(_ root: TreeNode?) -> Int {
        return sumNumbersHelper(root, 0)
    }

    private func sumNumbersHelper(_ root: TreeNode?, _ sum: Int) -> Int {
        guard let root = root else { return 0 }
        let currentSum = sum * 10 + root.val
        if root.left == nil && root.right == nil {
            return currentSum
        }
        return sumNumbersHelper(root.left, currentSum) + sumNumbersHelper(root.right, currentSum)
    }
}
```


### The End

