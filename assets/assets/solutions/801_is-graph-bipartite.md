# Is Graph Bipartite?

## Problem Statement

Given an undirected graph, represented as an adjacency list `graph`, determine if the graph is bipartite. A graph is bipartite if the nodes can be partitioned into two independent sets such that every edge connects a node in one set to a node in the other set.

## Input

```text
graph = [[1,3], [0,2], [1,3], [0,2]]
```

## Output

```text
true
```

## Solutions

### Dart

```dart
import 'dart:collection';

bool isBipartite(List<List<int>> graph) {
  List<int> color = List.filled(graph.length, 0);

  bool bfs(int start) {
    Queue<int> queue = Queue();
    queue.add(start);
    color[start] = 1;

    while (queue.isNotEmpty) {
      int node = queue.removeFirst();
      for (int neighbor in graph[node]) {
        if (color[neighbor] == color[node]) {
          return false;
        } else if (color[neighbor] == 0) {
          color[neighbor] = -color[node];
          queue.add(neighbor);
        }
      }
    }

    return true;
  }

  for (int i = 0; i < graph.length; i++) {
    if (color[i] == 0 && !bfs(i)) {
      return false;
    }
  }

  return true;
}
```

### C#

```csharp
public class Solution {
    public bool IsBipartite(int[][] graph) {
        int[] color = new int[graph.Length];

        bool Bfs(int start) {
            Queue<int> queue = new Queue<int>();
            queue.Enqueue(start);
            color[start] = 1;

            while (queue.Count > 0) {
                int node = queue.Dequeue();
                foreach (int neighbor in graph[node]) {
                    if (color[neighbor] == color[node]) {
                        return false;
                    } else if (color[neighbor] == 0) {
                        color[neighbor] = -color[node];
                        queue.Enqueue(neighbor);
                    }
                }
            }

            return true;
        }

        for (int i = 0; i < graph.Length; i++) {
            if (color[i] == 0 && !Bfs(i)) {
                return false;
            }
        }

        return true;
    }
}
```

### Java

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public boolean isBipartite(int[][] graph) {
        int[] color = new int[graph.length];

        for (int i = 0; i < graph.length; i++) {
            if (color[i] == 0) {
                Queue<Integer> queue = new LinkedList<>();
                queue.add(i);
                color[i] = 1;

                while (!queue.isEmpty()) {
                    int node = queue.poll();
                    for (int neighbor : graph[node]) {
                        if (color[neighbor] == color[node]) {
                            return false;
                        } else if (color[neighbor] == 0) {
                            color[neighbor] = -color[node];
                            queue.add(neighbor);
                        }
                    }
                }
            }
        }

        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isBipartite(graph: Array<IntArray>): Boolean {
        val color = IntArray(graph.size)

        fun bfs(start: Int): Boolean {
            val q = LinkedList<Int>()
            q.addFirst(start)
            color[start] = 1

            while (q.isNotEmpty()) {
                val n = q.removeLast()
                for (next in graph[n]) {
                    if (color[next] == color[n]) {
                        return false
                    } else if (color[next] == 0) {
                        color[next] = -color[n]
                        q.addFirst(next)
                    }
                }
            }
            return true
        }

        for (i in graph.indices) {
            if (color[i] == 0 && !bfs(i)) {
                return false
            }
        }

        return true
    }
}
```

### Swift

```swift
class Solution {
    func isBipartite(_ graph: [[Int]]) -> Bool {
        var color = [Int](repeating: 0, count: graph.count)

        func bfs(_ start: Int) -> Bool {
            var queue = [start]
            color[start] = 1

            while !queue.isEmpty {
                let node = queue.removeFirst()
                for neighbor in graph[node] {
                    if color[neighbor] == color[node] {
                        return false
                    } else if color[neighbor] == 0 {
                        color[neighbor] = -color[node]
                        queue.append(neighbor)
                    }
                }
            }

            return true
        }

        for i in 0..<graph.count {
            if color[i] == 0 && !bfs(i) {
                return false
            }
        }

        return true
    }
}
```

### The End