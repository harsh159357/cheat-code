# All Nodes Distance K in Binary Tree

## Problem Statement

Given the `root` of a binary tree, the `target` node, and an integer `k`, return a list of the values of all nodes that have a distance `k` from the target node.

## Input

```text
root = [3, 5, 1, 6, 2, 0, 8, null, null, 7, 4]
target = 5
k = 2
```

## Output

```text
[7, 4, 1]
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

List<int> distanceK(TreeNode? root, TreeNode? target, int k) {
  Map<int, List<int>> graph = {};

  void addNeighbor(int node, int neighbor) {
    graph.putIfAbsent(node, () => []).add(neighbor);
  }

  void dfs(TreeNode? node) {
    if (node == null) return;

    if (node.left != null) {
      addNeighbor(node.val, node.left!.val);
      addNeighbor(node.left!.val, node.val);
      dfs(node.left);
    }

    if (node.right != null) {
      addNeighbor(node.val, node.right!.val);
      addNeighbor(node.right!.val, node.val);
      dfs(node.right);
    }
  }

  dfs(root);

  Set<int> seen = {};
  List<int> queue = [];
  queue.add(target!.val);
  int level = 0;

  while (queue.isNotEmpty) {
    int levelSize = queue.length;
    List<int> result = [];
    for (int i = 0; i < levelSize; i++) {
      int node = queue.removeAt(0);
      seen.add(node);
      result.add(node);

      for (int neighbor in graph[node] ?? []) {
        if (!seen.contains(neighbor)) {
          seen.add(neighbor);
          queue.add(neighbor);
        }
      }
    }

    if (level == k) return result;
    level++;
  }

  return [];
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
    public IList<int> DistanceK(TreeNode root, TreeNode target, int k) {
        var graph = new Dictionary<int, List<int>>();

        void AddNeighbor(int node, int neighbor) {
            if (!graph.ContainsKey(node)) graph[node] = new List<int>();
            graph[node].Add(neighbor);
        }

        void BuildGraph(TreeNode node) {
            if (node == null) return;

            if (node.left != null) {
                AddNeighbor(node.val, node.left.val);
                AddNeighbor(node.left.val, node.val);
                BuildGraph(node.left);
            }

            if (node.right != null) {
                AddNeighbor(node.val, node.right.val);
                AddNeighbor(node.right.val, node.val);
                BuildGraph(node.right);
            }
        }

        BuildGraph(root);

        var seen = new HashSet<int>();
        var queue = new Queue<int>();
        queue.Enqueue(target.val);
        int level = 0;

        while (queue.Count > 0) {
            int size = queue.Count;
            var result = new List<int>();

            for (int i = 0; i < size; i++) {
                int node = queue.Dequeue();
                seen.Add(node);
                result.Add(node);

                foreach (var neighbor in graph[node]) {
                    if (!seen.Contains(neighbor)) {
                        seen.Add(neighbor);
                        queue.Enqueue(neighbor);
                    }
                }
            }

            if (level == k) return result;
            level++;
        }

        return new List<int>();
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
    public List<Integer> distanceK(TreeNode root, TreeNode target, int k) {
        Map<Integer, List<Integer>> graph = new HashMap<>();

        void addNeighbor(int node, int neighbor) {
            graph.computeIfAbsent(node, x -> new ArrayList<>()).add(neighbor);
        }

        void dfs(TreeNode node) {
            if (node == null) return;

            if (node.left != null) {
                addNeighbor(node.val, node.left.val);
                addNeighbor(node.left.val, node.val);
                dfs(node.left);
            }

            if (node.right != null) {
                addNeighbor(node.val, node.right.val);
                addNeighbor(node.right.val, node.val);
                dfs(node.right);
            }
        }

        dfs(root);

        Set<Integer> seen = new HashSet<>();
        Queue<Integer> queue = new LinkedList<>();
        queue.add(target.val);
        int level = 0;

        while (!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> result = new ArrayList<>();

            for (int i = 0; i < size; i++) {
                int node = queue.poll();
                seen.add(node);
                result.add(node);

                for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                    if (!seen.contains(neighbor)) {
                        seen.add(neighbor);
                        queue.add(neighbor);
                    }
                }
            }

            if (level == k) return result;
            level++;
        }

        return new ArrayList<>();
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
    func distanceK(_ root: TreeNode?, _ target: TreeNode?, _ k: Int) -> [Int] {
        var graph = [Int: [Int]]()

        func addNeighbor(_ node: Int, _ neighbor: Int) {
            graph[node, default: []].append(neighbor)
        }

        func dfs(_ node: TreeNode?) {
            guard let node = node else { return }

            if let left = node.left {
                addNeighbor(node.val, left.val)
                addNeighbor(left.val, node.val)
                dfs(left)
            }

            if let right = node.right {
                addNeighbor(node.val, right.val)
                addNeighbor(right.val, node.val)
                dfs(right)
            }
        }

        dfs(root)

        var seen = Set<Int>()
        var queue = [Int]()
        if let target = target {
            queue.append(target.val)
        }
        var level = 0

        while !queue.isEmpty {
            let size = queue.count
            var result = [Int]()

            for _ in 0..<size {
                let node = queue.removeFirst()
                seen.insert(node)
                result.append(node)

                for neighbor in graph[node, default: []] {
                    if !seen.contains(neighbor) {
                        seen.insert(neighbor)
                        queue.append(neighbor)
                    }
                }
            }

            if level == k {
                return result
            }
            level += 1
        }

        return []
    }
}
```

### The End