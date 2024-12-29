# Clone Graph

## Problem Statement

Given a reference of a node in a **connected undirected graph**, return a **deep copy (clone)** of the graph. Each node in the graph contains a value (`int`) and a list (`List[Node]`) of its neighbors.

---

## Input

```text
adjList = [[2, 4], [1, 3], [2, 4], [1, 3]]
```

## Output

```text
[[2, 4], [1, 3], [2, 4], [1, 3]]
```

## Solutions

### Dart

```dart
class Node {
  int val;
  List<Node?> neighbors;

  Node(this.val) : neighbors = [];
}

Node? cloneGraph(Node? node) {
  if (node == null) return null;
  Map<int, Node> visited = {};

  Node dfs(Node n) {
    if (visited.containsKey(n.val)) return visited[n.val]!;
    Node clone = Node(n.val);
    visited[n.val] = clone;
    for (var neighbor in n.neighbors) {
      if (neighbor != null) {
        clone.neighbors.add(dfs(neighbor));
      }
    }
    return clone;
  }

  return dfs(node);
}
```


### C#

```csharp
public class Node {
    public int val;
    public IList<Node> neighbors;

    public Node() {
        val = 0;
        neighbors = new List<Node>();
    }

    public Node(int _val) {
        val = _val;
        neighbors = new List<Node>();
    }

    public Node(int _val, List<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}

public class Solution {
    public Node CloneGraph(Node node) {
        if (node == null) return null;
        var visited = new Dictionary<int, Node>();

        Node DFS(Node n) {
            if (visited.ContainsKey(n.val)) return visited[n.val];
            var clone = new Node(n.val);
            visited[n.val] = clone;
            foreach (var neighbor in n.neighbors) {
                clone.neighbors.Add(DFS(neighbor));
            }
            return clone;
        }

        return DFS(node);
    }
}
```


### Java

```java
class Node {
    public int val;
    public List<Node> neighbors;

    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }

    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }

    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}

class Solution {
    public Node cloneGraph(Node node) {
        if (node == null) return null;
        Map<Integer, Node> visited = new HashMap<>();

        Node dfs(Node n) {
            if (visited.containsKey(n.val)) return visited.get(n.val);
            Node clone = new Node(n.val);
            visited.put(n.val, clone);
            for (Node neighbor : n.neighbors) {
                clone.neighbors.add(dfs(neighbor));
            }
            return clone;
        }

        return dfs(node);
    }
}
```


### Kotlin

```kotlin
class Node(var `val`: Int) {
    var neighbors: ArrayList<Node?> = ArrayList()
}

class Solution {
    fun cloneGraph(node: Node?): Node? {
        if (node == null) return null
        val visited = mutableMapOf<Int, Node>()

        fun dfs(n: Node): Node {
            if (visited.containsKey(n.`val`)) return visited[n.`val`]!!
            val clone = Node(n.`val`)
            visited[n.`val`] = clone
            for (neighbor in n.neighbors) {
                if (neighbor != null) {
                    clone.neighbors.add(dfs(neighbor))
                }
            }
            return clone
        }

        return dfs(node)
    }
}
```


### Swift

```swift
class Node {
    public var val: Int
    public var neighbors: [Node?]

    public init(_ val: Int) {
        self.val = val
        self.neighbors = []
    }
}

class Solution {
    func cloneGraph(_ node: Node?) -> Node? {
        guard let node = node else { return nil }
        var visited = [Int: Node]()

        func dfs(_ n: Node) -> Node {
            if let clone = visited[n.val] {
                return clone
            }
            let clone = Node(n.val)
            visited[n.val] = clone
            for neighbor in n.neighbors {
                if let neighbor = neighbor {
                    clone.neighbors.append(dfs(neighbor))
                }
            }
            return clone
        }

        return dfs(node)
    }
}
```


### The End

