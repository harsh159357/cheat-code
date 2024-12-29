# Reorder Routes to Make All Paths Lead to the City Zero

## Problem Statement

You are given `n` cities numbered from `0` to `n-1` and a list of `connections` where `connections[i] = [a, b]` represents a directed road from city `a` to city `b`. You can reorder the roads in any direction.

Return the minimum number of edges changed to make all paths lead to city `0`.

## Input

```text
n = 6
connections = [[0,1],[1,3],[2,3],[4,0],[4,5]]
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun minReorder(n: Int, connections: Array<IntArray>): Int {
        val graph = Array(n) { mutableListOf<Pair<Int, Int>>() }
        for (conn in connections) {
            graph[conn[0]].add(conn[1] to 1) // Forward edge with cost 1
            graph[conn[1]].add(conn[0] to 0) // Reverse edge with cost 0
        }
        return dfs(graph, 0, -1)
    }

    private fun dfs(graph: Array<MutableList<Pair<Int, Int>>>, node: Int, parent: Int): Int {
        var changes = 0
        for (neighbor in graph[node]) {
            if (neighbor.first != parent) {
                changes += neighbor.second
                changes += dfs(graph, neighbor.first, node)
            }
        }
        return changes
    }
}
```

### Dart

```dart
int minReorder(int n, List<List<int>> connections) {
  List<List<List<int>>> graph = List.generate(n, (_) => []);
  for (var conn in connections) {
    graph[conn[0]].add([conn[1], 1]); // Forward edge with cost 1
    graph[conn[1]].add([conn[0], 0]); // Reverse edge with cost 0
  }

  int dfs(int node, int parent) {
    int changes = 0;
    for (var neighbor in graph[node]) {
      if (neighbor[0] != parent) {
        changes += neighbor[1];
        changes += dfs(neighbor[0], node);
      }
    }
    return changes;
  }

  return dfs(0, -1);
}
```

### C#

```csharp
public class Solution {
    public int MinReorder(int n, int[][] connections) {
        var graph = new List<(int, int)>[n];
        for (int i = 0; i < n; i++) graph[i] = new List<(int, int)>();

        foreach (var conn in connections) {
            graph[conn[0]].Add((conn[1], 1)); // Forward edge with cost 1
            graph[conn[1]].Add((conn[0], 0)); // Reverse edge with cost 0
        }

        int Dfs(int node, int parent) {
            int changes = 0;
            foreach (var (neighbor, cost) in graph[node]) {
                if (neighbor != parent) {
                    changes += cost;
                    changes += Dfs(neighbor, node);
                }
            }
            return changes;
        }

        return Dfs(0, -1);
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int minReorder(int n, int[][] connections) {
        List<List<int[]>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        for (int[] conn : connections) {
            graph.get(conn[0]).add(new int[]{conn[1], 1}); // Forward edge with cost 1
            graph.get(conn[1]).add(new int[]{conn[0], 0}); // Reverse edge with cost 0
        }

        return dfs(graph, 0, -1);
    }

    private int dfs(List<List<int[]>> graph, int node, int parent) {
        int changes = 0;
        for (int[] neighbor : graph.get(node)) {
            if (neighbor[0] != parent) {
                changes += neighbor[1];
                changes += dfs(graph, neighbor[0], node);
            }
        }
        return changes;
    }
}
```

### Swift

```swift
class Solution {
    func minReorder(_ n: Int, _ connections: [[Int]]) -> Int {
        var graph = Array(repeating: [(Int, Int)](), count: n)
        for conn in connections {
            graph[conn[0]].append((conn[1], 1)) // Forward edge with cost 1
            graph[conn[1]].append((conn[0], 0)) // Reverse edge with cost 0
        }

        func dfs(_ node: Int, _ parent: Int) -> Int {
            var changes = 0
            for (neighbor, cost) in graph[node] {
                if neighbor != parent {
                    changes += cost
                    changes += dfs(neighbor, node)
                }
            }
            return changes
        }

        return dfs(0, -1)
    }
}
```

### The End