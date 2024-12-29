# Unique Binary Search Trees II

## Problem Statement

Given an integer `n`, return all the structurally unique BST's (binary search trees) which have exactly `n` nodes of unique values from `1` to `n`. Return the answer in any order.

## Input

```text
n = 3
```

## Output

```text
[[1,null,2,null,3],[1,null,3,2],[2,1,3],[3,1,null,null,2],[3,2,null,1]]
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

List<TreeNode?> generateTrees(int n) {
  if (n == 0) return [];
  return _generateTrees(1, n);
}

List<TreeNode?> _generateTrees(int start, int end) {
  List<TreeNode?> result = [];
  if (start > end) {
    result.add(null);
    return result;
  }
  for (int i = start; i <= end; i++) {
    List<TreeNode?> leftTrees = _generateTrees(start, i - 1);
    List<TreeNode?> rightTrees = _generateTrees(i + 1, end);
    for (TreeNode? left in leftTrees) {
      for (TreeNode? right in rightTrees) {
        TreeNode root = TreeNode(i);
        root.left = left;
        root.right = right;
        result.add(root);
      }
    }
  }
  return result;
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
    public IList<TreeNode> GenerateTrees(int n) {
        if (n == 0) return new List<TreeNode>();
        return GenerateTrees(1, n);
    }

    private IList<TreeNode> GenerateTrees(int start, int end) {
        var result = new List<TreeNode>();
        if (start > end) {
            result.Add(null);
            return result;
        }
        for (int i = start; i <= end; i++) {
            var leftTrees = GenerateTrees(start, i - 1);
            var rightTrees = GenerateTrees(i + 1, end);
            foreach (var left in leftTrees) {
                foreach (var right in rightTrees) {
                    var root = new TreeNode(i);
                    root.left = left;
                    root.right = right;
                    result.Add(root);
                }
            }
        }
        return result;
    }
}
```

### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int val) { this.val = val; this.left = null; this.right = null; }
}

class Solution {
    public List<TreeNode> generateTrees(int n) {
        if (n == 0) return new ArrayList<>();
        return generateTrees(1, n);
    }

    private List<TreeNode> generateTrees(int start, int end) {
        List<TreeNode> result = new ArrayList<>();
        if (start > end) {
            result.add(null);
            return result;
        }
        for (int i = start; i <= end; i++) {
            List<TreeNode> leftTrees = generateTrees(start, i - 1);
            List<TreeNode> rightTrees = generateTrees(i + 1, end);
            for (TreeNode left : leftTrees) {
                for (TreeNode right : rightTrees) {
                    TreeNode root = new TreeNode(i);
                    root.left = left;
                    root.right = right;
                    result.add(root);
                }
            }
        }
        return result;
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
    fun generateTrees(n: Int): List<TreeNode?> {
        if (n == 0) return emptyList()
        return generateTrees(1, n)
    }

    private fun generateTrees(start: Int, end: Int): List<TreeNode?> {
        val result = mutableListOf<TreeNode?>()
        if (start > end) {
            result.add(null)
            return result
        }
        for (i in start..end) {
            val leftTrees = generateTrees(start, i - 1)
            val rightTrees = generateTrees(i + 1, end)
            for (left in leftTrees) {
                for (right in rightTrees) {
                    val root = TreeNode(i)
                    root.left = left
                    root.right = right
                    result.add(root)
                }
            }
        }
        return result
    }
}
```

### Swift

```swift
class TreeNode {
    var val: Int
    var left: TreeNode?
    var right: TreeNode?
    init(_ val: Int) {
        self.val = val
        self.left = nil
        self.right = nil
    }
}

class Solution {
    func generateTrees(_ n: Int) -> [TreeNode?] {
        if n == 0 { return [] }
        return generateTrees(1, n)
    }

    private func generateTrees(_ start: Int, _ end: Int) -> [TreeNode?] {
        var result = [TreeNode?]()
        if start > end {
            result.append(nil)
            return result
        }
        for i in start...end {
            let leftTrees = generateTrees(start, i - 1)
            let rightTrees = generateTrees(i + 1, end)
            for left in leftTrees {
                for right in rightTrees {
                    let root = TreeNode(i)
                    root.left = left
                    root.right = right
                    result.append(root)
                }
            }
        }
        return result
    }
}
```

### The End

