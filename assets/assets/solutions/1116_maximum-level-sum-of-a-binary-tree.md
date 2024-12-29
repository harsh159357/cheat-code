# Maximum Level Sum of a Binary Tree

## Problem Statement

Given the root of a binary tree, return the level (1-indexed) that has the maximum sum of node values.

---

## Input

```text
root = [1, 2, 3, 4, 5, 6, 7]
```

## Output

```text
2
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxLevelSum(root: TreeNode?): Int {
        if (root == null) return -1
        var maxLevel = 0
        var maxSum = Int.MIN_VALUE
        var level = 1
        val queue = LinkedList<TreeNode>()
        queue.offer(root)
        while (queue.isNotEmpty()) {
            val size = queue.size
            var levelSum = 0
            for (i in 0 until size) {
                val node = queue.poll()
                levelSum += node.`val`
                node.left?.let { queue.offer(it) }
                node.right?.let { queue.offer(it) }
            }
            if (levelSum > maxSum) {
                maxSum = levelSum
                maxLevel = level
            }
            level++
        }
        return maxLevel
    }
}
```


### Dart

```dart
class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;
  TreeNode(this.val);
}

class Solution {
  int maxLevelSum(TreeNode? root) {
    if (root == null) return -1;
    
    int maxLevel = 0;
    int maxSum = -99999999;
    int level = 1;
    List<TreeNode> queue = [root!];
    
    while (queue.isNotEmpty) {
      int size = queue.length;
      int levelSum = 0;
      
      for (int i = 0; i < size; i++) {
        TreeNode node = queue.removeAt(0);
        levelSum += node.val;
        if (node.left != null) queue.add(node.left!);
        if (node.right != null) queue.add(node.right!);
      }
      
      if (levelSum > maxSum) {
        maxSum = levelSum;
        maxLevel = level;
      }
      
      level++;
    }
    
    return maxLevel;
  }
}
```


### C#

```csharp
using System;
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
    public int MaxLevelSum(TreeNode root) {
        if (root == null) return -1;
        
        int maxLevel = 0;
        int maxSum = Int32.MinValue;
        int level = 1;
        Queue<TreeNode> queue = new Queue<TreeNode>();
        queue.Enqueue(root);
        
        while (queue.Count > 0) {
            int size = queue.Count;
            int levelSum = 0;
            
            for (int i = 0; i < size; i++) {
                TreeNode node = queue.Dequeue();
                levelSum += node.val;
                if (node.left != null) queue.Enqueue(node.left);
                if (node.right != null) queue.Enqueue(node.right);
            }
            
            if (levelSum > maxSum) {
                maxSum = levelSum;
                maxLevel = level;
            }
            
            level++;
        }
        
        return maxLevel;
    }
}
```


### Java

```java
import java.util.*;

public class Solution {
    public int maxLevelSum(TreeNode root) {
        if (root == null) return -1;

        int maxLevel = 0;
        int maxSum = Integer.MIN_VALUE;
        int level = 1;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            int size = queue.size();
            int levelSum = 0;

            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                levelSum += node.val;
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }

            if (levelSum > maxSum) {
                maxSum = levelSum;
                maxLevel = level;
            }

            level++;
        }

        return maxLevel;
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
    func maxLevelSum(_ root: TreeNode?) -> Int {
        guard let root = root else { return -1 }
        
        var maxLevel = 0
        var maxSum = Int.min
        var level = 1
        var queue: [TreeNode] = [root]
        
        while !queue.isEmpty {
            let size = queue.count
            var levelSum = 0
            
            for _ in 0..<size {
                let node = queue.removeFirst()
                levelSum += node.val
                if let left = node.left { queue.append(left) }
                if let right = node.right { queue.append(right) }
            }
            
            if levelSum > maxSum {
                maxSum = levelSum
                maxLevel = level
            }
            
            level += 1
        }
        
        return maxLevel
    }
}
```


### The End