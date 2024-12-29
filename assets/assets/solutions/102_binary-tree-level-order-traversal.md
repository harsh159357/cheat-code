# Binary Tree Level Order Traversal

## Problem Statement

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

## Input

```text
root = [3, 9, 20, null, null, 15, 7]
```

## Output

```text
[
  [3],
  [9, 20],
  [15, 7]
]
```


## Solutions

### Dart

```dart
import 'dart:collection';

class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;

  TreeNode(this.val, [this.left, this.right]);
}

List<List<int>> levelOrder(TreeNode? root) {
  List<List<int>> result = [];
  if (root == null) return result;

  Queue<TreeNode> queue = Queue();
  queue.add(root);

  while (queue.isNotEmpty) {
    int size = queue.length;
    List<int> level = [];

    for (int i = 0; i < size; i++) {
      TreeNode node = queue.removeFirst();
      level.add(node.val);

      if (node.left != null) queue.add(node.left!);
      if (node.right != null) queue.add(node.right!);
    }

    result.add(level);
  }

  return result;
}
```


### C#

```csharp
using System.Collections.Generic;

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
    public IList<IList<int>> LevelOrder(TreeNode root) {
        var result = new List<IList<int>>();
        if (root == null) return result;

        var queue = new Queue<TreeNode>();
        queue.Enqueue(root);

        while (queue.Count > 0) {
            int size = queue.Count;
            var level = new List<int>();

            for (int i = 0; i < size; i++) {
                var node = queue.Dequeue();
                level.Add(node.val);

                if (node.left != null) queue.Enqueue(node.left);
                if (node.right != null) queue.Enqueue(node.right);
            }

            result.Add(level);
        }

        return result;
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
    TreeNode() {}
    TreeNode(int val) { this.val = val; }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) return result;

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> level = new ArrayList<>();

            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                level.add(node.val);

                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }

            result.add(level);
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
    fun levelOrder(root: TreeNode?): List<List<Int>> {
        val result = mutableListOf<List<Int>>()
        if (root == null) return result

        val queue: Queue<TreeNode> = LinkedList()
        queue.offer(root)

        while (queue.isNotEmpty()) {
            val size = queue.size
            val level = mutableListOf<Int>()

            repeat(size) {
                val node = queue.poll()
                level.add(node.`val`)
                node.left?.let { queue.offer(it) }
                node.right?.let { queue.offer(it) }
            }

            result.add(level)
        }

        return result
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
    func levelOrder(_ root: TreeNode?) -> [[Int]] {
        var result = [[Int]]()
        guard let root = root else { return result }

        var queue = [TreeNode]()
        queue.append(root)

        while !queue.isEmpty {
            let size = queue.count
            var level = [Int]()

            for _ in 0..<size {
                let node = queue.removeFirst()
                level.append(node.val)

                if let left = node.left {
                    queue.append(left)
                }
                if let right = node.right {
                    queue.append(right)
                }
            }

            result.append(level)
        }

        return result
    }
}
```

### The End




