# Critical Connections in a Network

## Problem Statement

You are given an integer `n` representing the number of nodes in a network and a list `connections` representing the connections between nodes where each connection is a pair of nodes. Find all the critical connections in the network.

A critical connection is an edge that, if removed, will make the graph disconnected.

## Input

```text
n = 4
connections = [[0, 1], [1, 2], [2, 0], [1, 3]]
```

## Output

```text
[[1, 3]]
```


## Solutions

### Kotlin

```kotlin
import kotlin.collections.ArrayList

class Solution {
    private var time = 0

    fun criticalConnections(n: Int, connections: List<List<Int>>): List<List<Int>> {
        val graph = Array(n) { mutableListOf<Int>() }
        for (conn in connections) {
            graph[conn[0]].add(conn[1])
            graph[conn[1]].add(conn[0])
        }

        val low = IntArray(n) { -1 }
        val disc = IntArray(n) { -1 }
        val visited = BooleanArray(n) { false }
        val bridges = mutableListOf<List<Int>>()

        for (i in 0 until n) {
            if (!visited[i]) {
                dfs(i, -1, graph, low, disc, visited, bridges)
            }
        }

        return bridges
    }

    private fun dfs(
        u: Int,
        parent: Int,
        graph: Array<MutableList<Int>>,
        low: IntArray,
        disc: IntArray,
        visited: BooleanArray,
        bridges: MutableList<List<Int>>
    ) {
        visited[u] = true
        disc[u] = time
        low[u] = time
        time++

        for (v in graph[u]) {
            if (!visited[v]) {
                dfs(v, u, graph, low, disc, visited, bridges)
                low[u] = minOf(low[u], low[v])
                if (low[v] > disc[u]) {
                    bridges.add(listOf(u, v))
                }
            } else if (v != parent) {
                low[u] = minOf(low[u], disc[v])
            }
        }
    }
}
```

### Dart

```dart
List<List<int>> criticalConnections(int n, List<List<int>> connections) {
  List<List<int>> graph = List.generate(n, (_) => []);
  for (var conn in connections) {
    graph[conn[0]].add(conn[1]);
    graph[conn[1]].add(conn[0]);
  }

  List<int> low = List.filled(n, -1);
  List<int> disc = List.filled(n, -1);
  List<bool> visited = List.filled(n, false);
  List<List<int>> bridges = [];

  int time = 0;

  void dfs(int u, int parent) {
    visited[u] = true;
    disc[u] = time;
    low[u] = time;
    time++;

    for (var v in graph[u]) {
      if (!visited[v]) {
        dfs(v, u);
        low[u] = low[u] < low[v] ? low[u] : low[v];
        if (low[v] > disc[u]) {
          bridges.add([u, v]);
        }
      } else if (v != parent) {
        low[u] = low[u] < disc[v] ? low[u] : disc[v];
      }
    }
  }

  for (int i = 0; i < n; i++) {
    if (!visited[i]) dfs(i, -1);
  }

  return bridges;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    private int time = 0;

    public IList<IList<int>> CriticalConnections(int n, IList<IList<int>> connections) {
        var graph = new List<int>[n];
        for (int i = 0; i < n; i++) {
            graph[i] = new List<int>();
        }

        foreach (var conn in connections) {
            graph[conn[0]].Add(conn[1]);
            graph[conn[1]].Add(conn[0]);
        }

        int[] low = new int[n];
        int[] disc = new int[n];
        bool[] visited = new bool[n];
        var bridges = new List<IList<int>>();

        void Dfs(int u, int parent) {
            visited[u] = true;
            disc[u] = time;
            low[u] = time;
            time++;

            foreach (var v in graph[u]) {
                if (!visited[v]) {
                    Dfs(v, u);
                    low[u] = Math.Min(low[u], low[v]);
                    if (low[v] > disc[u]) {
                        bridges.Add(new List<int> { u, v });
                    }
                } else if (v != parent) {
                    low[u] = Math.Min(low[u], disc[v]);
                }
            }
        }

        for (int i = 0; i < n; i++) {
            if (!visited[i]) Dfs(i, -1);
        }

        return bridges;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    private int time = 0;

    public List<List<Integer>> criticalConnections(int n, List<List<Integer>> connections) {
        List<Integer>[] graph = new ArrayList[n];
        for (int i = 0; i < n; i++) {
            graph[i] = new ArrayList<>();
        }

        for (List<Integer> conn : connections) {
            graph[conn.get(0)].add(conn.get(1));
            graph[conn.get(1)].add(conn.get(0));
        }

        int[] low = new int[n];
        int[] disc = new int[n];
        boolean[] visited = new boolean[n];
        List<List<Integer>> bridges = new ArrayList<>();

        dfs(0, -1, graph, low, disc, visited, bridges);
        return bridges;
    }

    private void dfs(int u, int parent, List<Integer>[] graph, int[] low, int[] disc, boolean[] visited, List<List<Integer>> bridges) {
        visited[u] = true;
        disc[u] = time;
        low[u] = time;
        time++;

        for (int v : graph[u]) {
            if (!visited[v]) {
                dfs(v, u, graph, low, disc, visited, bridges);
                low[u] = Math.min(low[u], low[v]);
                if (low[v] > disc[u]) {
                    bridges.add(Arrays.asList(u, v));
                }
            } else if (v != parent) {
                low[u] = Math.min(low[u], disc[v]);
            }
        }
    }
}
```

### Swift

```swift
class Solution {
    private var time = 0

    func criticalConnections(_ n: Int, _ connections: [[Int]]) -> [[Int]] {
        var graph = Array(repeating: [Int](), count: n)
        for conn in connections {
            graph[conn[0]].append(conn[1])
            graph[conn[1]].append(conn[0])
        }

        var low = Array(repeating: -1, count: n)
        var disc = Array(repeating: -1, count: n)
        var visited = Array(repeating: false, count: n)
        var bridges = [[Int]]()

        func dfs(_ u: Int, _ parent: Int) {
            visited[u] = true
            disc[u] = time
            low[u] = time
            time += 1

            for v in graph[u] {
                if !visited[v] {
                    dfs(v, u)
                    low[u] = min(low[u], low[v])
                    if low[v] > disc[u] {
                        bridges.append([u, v])
                    }
                } else if v != parent {
                    low[u] = min(low[u], disc[v])
                }
            }
        }

        for i in 0..<n {
            if !visited[i] {
                dfs(i, -1)
            }
        }

        return bridges
    }
}
```

### The End