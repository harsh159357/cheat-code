# Binary Tree Right Side View

## Problem Statement

Given the `root` of a binary tree, imagine yourself standing on the right side of it. Return the values of the nodes you can see ordered from top to bottom.

## Input

```text
root = [1,2,3,null,5,null,4]
```

## Output

```text
[1, 3, 4]
```

## Solutions

### Dart

```dart
import 'dart:collection';

List<int> rightSideView(TreeNode? root) {
  List<int> result = [];
  if (root == null) return result;
  Queue<TreeNode> queue = Queue<TreeNode>();
  queue.add(root);
  while (queue.isNotEmpty) {
    int size = queue.length;
    for (int i = 0; i < size; i++) {
      TreeNode node = queue.removeFirst();
      if (i == size - 1) result.add(node.val);
      if (node.left != null) queue.add(node.left!);
      if (node.right != null) queue.add(node.right!);
    }
  }
  return result;
}

class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;
  TreeNode(this.val, [this.left, this.right]);
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public IList<int> RightSideView(TreeNode root) {
        var result = new List<int>();
        if (root == null) return result;
        var queue = new Queue<TreeNode>();
        queue.Enqueue(root);
        while (queue.Count > 0) {
            int size = queue.Count;
            for (int i = 0; i < size; i++) {
                var node = queue.Dequeue();
                if (i == size - 1) result.Add(node.val);
                if (node.left != null) queue.Enqueue(node.left);
                if (node.right != null) queue.Enqueue(node.right);
            }
        }
        return result;
    }
}

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
```

### Java

```java
import java.util.*;

class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if (root == null) return result;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                if (i == size - 1) result.add(node.val);
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }
        }
        return result;
    }
}

class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}
```

### Kotlin

```kotlin
class Solution {
    fun rightSideView(root: TreeNode?): List<Int> {
        val result = mutableListOf<Int>()
        if (root == null) return result
        val queue = LinkedList<TreeNode>()
        queue.offer(root)
        while (queue.isNotEmpty()) {
            val size = queue.size
            for (i in 0 until size) {
                val node = queue.poll()
                if (i == size - 1) result.add(node.`val`)
                node.left?.let { queue.offer(it) }
                node.right?.let { queue.offer(it) }
            }
        }
        return result
    }
}

class TreeNode(var `val`: Int) {
    var left: TreeNode? = null
    var right: TreeNode? = null
}
```

### Swift

```swift
class Solution {
    func rightSideView(_ root: TreeNode?) -> [Int] {
        var result = [Int]()
        guard let root = root else { return result }
        var queue = [TreeNode]()
        queue.append(root)
        while !queue.isEmpty {
            let size = queue.count
            for i in 0..<size {
                let node = queue.removeFirst()
                if i == size - 1 {
                    result.append(node.val)
                }
                if let left = node.left {
                    queue.append(left)
                }
                if let right = node.right {
                    queue.append(right)
                }
            }
        }
        return result
    }
}

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
```


### The End

