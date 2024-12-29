# Find Eventual Safe States

## Problem Statement

Given a directed graph, where `graph[i]` is a list of nodes that node `i` can directly reach, determine all the "safe nodes". A node is safe if it is eventually leads to a terminal node (a node with no outgoing edges) or a node that only leads to other safe nodes.

Return the list of safe nodes in increasing order.

## Input

```text
graph = [[1, 2], [2, 3], [5], [0], [], [], []]
```

## Output

```text
[2, 4, 5, 6]
```


## Solutions

### Dart

```dart
List<int> eventualSafeNodes(List<List<int>> graph) {
  int n = graph.length;
  List<int> visited = List.filled(n, 0);
  List<int> result = [];

  bool dfs(int node) {
    if (visited[node] == 1) return true; // Already visited and safe
    if (visited[node] == 2) return false; // Visiting (cycle detected)

    visited[node] = 2; // Mark as visiting

    for (int next in graph[node]) {
      if (!dfs(next)) return false;
    }

    visited[node] = 1; // Mark as visited and safe
    return true;
  }

  for (int i = 0; i < n; i++) {
    if (dfs(i)) result.add(i);
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public IList<int> EventualSafeNodes(int[][] graph) {
        int n = graph.Length;
        int[] visited = new int[n];
        List<int> result = new List<int>();

        bool Dfs(int node) {
            if (visited[node] == 1) return true; // Already visited and safe
            if (visited[node] == 2) return false; // Visiting (cycle detected)

            visited[node] = 2; // Mark as visiting

            foreach (int next in graph[node]) {
                if (!Dfs(next)) return false;
            }

            visited[node] = 1; // Mark as visited and safe
            return true;
        }

        for (int i = 0; i < n; i++) {
            if (Dfs(i)) result.Add(i);
        }

        return result;
    }
}
```

### Java

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> eventualSafeNodes(int[][] graph) {
        int n = graph.length;
        int[] visited = new int[n];
        List<Integer> result = new ArrayList<>();

        boolean dfs(int node) {
            if (visited[node] == 1) return true; // Already visited and safe
            if (visited[node] == 2) return false; // Visiting (cycle detected)

            visited[node] = 2; // Mark as visiting

            for (int next : graph[node]) {
                if (!dfs(next)) return false;
            }

            visited[node] = 1; // Mark as visited and safe
            return true;
        }

        for (int i = 0; i < n; i++) {
            if (dfs(i)) result.add(i);
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun eventualSafeNodes(graph: Array<IntArray>): List<Int> {
        val n = graph.size
        val visited = IntArray(n)
        val result = mutableListOf<Int>()

        fun dfs(node: Int): Boolean {
            if (visited[node] == 1) return true // Already visited and safe
            if (visited[node] == 2) return false // Currently being visited (cycle detected)

            visited[node] = 2 // Mark as visiting

            for (next in graph[node]) {
                if (!dfs(next)) return false // Check if cycle detected in the next node
            }

            visited[node] = 1 // Mark as visited and safe
            return true
        }

        for (i in 0 until n) {
            if (dfs(i)) result.add(i)
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func eventualSafeNodes(_ graph: [[Int]]) -> [Int] {
        let n = graph.count
        var visited = [Int](repeating: 0, count: n)
        var result = [Int]()

        func dfs(_ node: Int) -> Bool {
            if visited[node] == 1 { return true } // Already visited and safe
            if visited[node] == 2 { return false } // Currently being visited (cycle detected)

            visited[node] = 2 // Mark as visiting

            for next in graph[node] {
                if !dfs(next) { return false } // Check if cycle detected in the next node
            }

            visited[node] = 1 // Mark as visited and safe
            return true
        }

        for i in 0..<n {
            if dfs(i) {
                result.append(i)
            }
        }

        return result
    }
}
```


### The End