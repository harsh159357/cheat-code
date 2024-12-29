# Average of Levels in Binary Tree

## Problem Statement

Given the `root` of a binary tree, return the average value of the nodes on each level in the form of an array.

## Input

```text
root = [3, 9, 20, null, null, 15, 7]
```

## Output

```text
[3.0, 14.5, 11.0]
```

## Solutions

### Kotlin

```kotlin
import java.util.LinkedList

class TreeNode(var `val`: Int) {
    var left: TreeNode? = null
    var right: TreeNode? = null
}

class Solution {
    fun averageOfLevels(root: TreeNode?): DoubleArray {
        val result = mutableListOf<Double>()
        if (root == null) return result.toDoubleArray()
        val queue = LinkedList<TreeNode>()
        queue.offer(root)
        while (queue.isNotEmpty()) {
            val size = queue.size
            var sum = 0.0
            for (i in 0 until size) {
                val node = queue.poll()
                sum += node.`val`
                node.left?.let { queue.offer(it) }
                node.right?.let { queue.offer(it) }
            }
            result.add(sum / size)
        }
        return result.toDoubleArray()
    }
}

fun main() {
    val root = TreeNode(3).apply {
        left = TreeNode(9)
        right = TreeNode(20).apply {
            left = TreeNode(15)
            right = TreeNode(7)
        }
    }
    val solution = Solution()
    println(solution.averageOfLevels(root).joinToString(", ")) // Output: [3.0, 14.5, 11.0]
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

List<double> averageOfLevels(TreeNode? root) {
  List<double> result = [];
  if (root == null) return result;
  Queue<TreeNode> queue = Queue();
  queue.add(root);
  while (queue.isNotEmpty) {
    int size = queue.length;
    double sum = 0;
    for (int i = 0; i < size; i++) {
      TreeNode node = queue.removeFirst();
      sum += node.val;
      if (node.left != null) queue.add(node.left!);
      if (node.right != null) queue.add(node.right!);
    }
    result.add(sum / size);
  }
  return result;
}

void main() {
  TreeNode root = TreeNode(3, TreeNode(9), TreeNode(20, TreeNode(15), TreeNode(7)));
  print(averageOfLevels(root)); // Output: [3.0, 14.5, 11.0]
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
    public IList<double> AverageOfLevels(TreeNode root) {
        var result = new List<double>();
        var queue = new Queue<TreeNode>();
        queue.Enqueue(root);
        while (queue.Count > 0) {
            int size = queue.Count;
            double sum = 0;
            for (int i = 0; i < size; i++) {
                var node = queue.Dequeue();
                sum += node.val;
                if (node.left != null) queue.Enqueue(node.left);
                if (node.right != null) queue.Enqueue(node.right);
            }
            result.Add(sum / size);
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
    TreeNode(int val) { this.val = val; }
}

class Solution {
    public List<Double> averageOfLevels(TreeNode root) {
        List<Double> result = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            int size = queue.size();
            double sum = 0;
            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                sum += node.val;
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }
            result.add(sum / size);
        }
        return result;
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
    func averageOfLevels(_ root: TreeNode?) -> [Double] {
        guard let root = root else { return [] }
        var result: [Double] = []
        var queue: [TreeNode] = [root]
        while !queue.isEmpty {
            let size = queue.count
            var sum = 0.0
            for _ in 0..<size {
                let node = queue.removeFirst()
                sum += Double(node.val)
                if let left = node.left {
                    queue.append(left)
                }
                if let right = node.right {
                    queue.append(right)
                }
            }
            result.append(sum / Double(size))
        }
        return result
    }
}

// Example usage
let root = TreeNode(3, TreeNode(9), TreeNode(20, TreeNode(15), TreeNode(7)))
let solution = Solution()
print(solution.averageOfLevels(root)) // Output: [3.0, 14.5, 11.0]
```

### The End