# Shortest Path with Alternating Colors

## Problem Statement

You are given an integer `n`, the number of nodes in a directed graph. Each node is labeled from `0` to `n - 1`. You are also given two arrays `redEdges` and `blueEdges` where:

- `redEdges[i] = [ai, bi]` indicates a directed edge from node `ai` to node `bi` in the red graph.
- `blueEdges[i] = [ui, vi]` indicates a directed edge from node `ui` to node `vi` in the blue graph.

Return an array `answer` of length `n` where `answer[x]` is the length of the shortest path from node `0` to node `x` such that the edge colors alternate along the path, or `-1` if such a path does not exist.

## Input

```text
n = 3
redEdges = [[0,1],[1,2]]
blueEdges = []
```

## Output

```text
[0,1,-1]
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun shortestAlternatingPaths(n: Int, redEdges: Array<IntArray>, blueEdges: Array<IntArray>): IntArray {
        val redAdj = mutableMapOf<Int, MutableList<Int>>()
        val blueAdj = mutableMapOf<Int, MutableList<Int>>()

        for ((s, d) in redEdges) {
            redAdj.getOrPut(s) { mutableListOf() }.add(d)
        }
        for ((s, d) in blueEdges) {
            blueAdj.getOrPut(s) { mutableListOf() }.add(d)
        }

        val queue = LinkedList<Triple<Int, Int, String>>()
        val visited = mutableSetOf<Pair<Int, String>>()
        queue.add(Triple(0, 0, "NA"))
        visited.add(Pair(0, "NA"))

        val paths = IntArray(n) { -1 }

        while (queue.isNotEmpty()) {
            val (node, distance, prevEdge) = queue.removeFirst()

            if (paths[node] == -1) {
                paths[node] = distance
            }

            if (prevEdge != "RED") {
                val children = redAdj.getOrDefault(node, emptyList())
                for (nei in children) {
                    val pair = nei to "RED"
                    if (pair !in visited) {
                        visited.add(pair)
                        queue.add(Triple(nei, distance + 1, "RED"))
                    }
                }
            }

            if (prevEdge != "BLUE") {
                val children = blueAdj.getOrDefault(node, emptyList())
                for (nei in children) {
                    val pair = nei to "BLUE"
                    if (pair !in visited) {
                        visited.add(pair)
                        queue.add(Triple(nei, distance + 1, "BLUE"))
                    }
                }
            }
        }

        return paths
    }
}
```

### Dart

```dart
List<int> shortestAlternatingPaths(int n, List<List<int>> redEdges, List<List<int>> blueEdges) {
  Map<int, List<int>> redAdj = {};
  Map<int, List<int>> blueAdj = {};

  for (var edge in redEdges) {
    redAdj.putIfAbsent(edge[0], () => []).add(edge[1]);
  }
  for (var edge in blueEdges) {
    blueAdj.putIfAbsent(edge[0], () => []).add(edge[1]);
  }

  Queue<List> queue = Queue();
  Set<List> visited = {};
  queue.add([0, 0, 'NA']);
  visited.add([0, 'NA']);

  List<int> paths = List.filled(n, -1);

  while (queue.isNotEmpty) {
    var current = queue.removeFirst();
    int node = current[0], distance = current[1];
    String prevEdge = current[2];

    if (paths[node] == -1) {
      paths[node] = distance;
    }

    if (prevEdge != 'RED') {
      for (var nei in redAdj[node] ?? []) {
        if (!visited.contains([nei, 'RED'])) {
          visited.add([nei, 'RED']);
          queue.add([nei, distance + 1, 'RED']);
        }
      }
    }

    if (prevEdge != 'BLUE') {
      for (var nei in blueAdj[node] ?? []) {
        if (!visited.contains([nei, 'BLUE'])) {
          visited.add([nei, 'BLUE']);
          queue.add([nei, distance + 1, 'BLUE']);
        }
      }
    }
  }

  return paths;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public int[] ShortestAlternatingPaths(int n, int[][] redEdges, int[][] blueEdges) {
        var redAdj = new Dictionary<int, List<int>>();
        var blueAdj = new Dictionary<int, List<int>>();

        foreach (var edge in redEdges) {
            if (!redAdj.ContainsKey(edge[0])) redAdj[edge[0]] = new List<int>();
            redAdj[edge[0]].Add(edge[1]);
        }

        foreach (var edge in blueEdges) {
            if (!blueAdj.ContainsKey(edge[0])) blueAdj[edge[0]] = new List<int>();
            blueAdj[edge[0]].Add(edge[1]);
        }

        var queue = new Queue<(int node, int distance, string prevEdge)>();
        var visited = new HashSet<(int node, string edge)>();
        queue.Enqueue((0, 0, "NA"));
        visited.Add((0, "NA"));

        var paths = new int[n];
        for (int i = 0; i < n; i++) paths[i] = -1;

        while (queue.Count > 0) {
            var (node, distance, prevEdge) = queue.Dequeue();

            if (paths[node] == -1) {
                paths[node] = distance;
            }

            if (prevEdge != "RED" && redAdj.ContainsKey(node)) {
                foreach (var neighbor in redAdj[node]) {
                    if (!visited.Contains((neighbor, "RED"))) {
                        visited.Add((neighbor, "RED"));
                        queue.Enqueue((neighbor, distance + 1, "RED"));
                    }
                }
            }

            if (prevEdge != "BLUE" && blueAdj.ContainsKey(node)) {
                foreach (var neighbor in blueAdj[node]) {
                    if (!visited.Contains((neighbor, "BLUE"))) {
                        visited.Add((neighbor, "BLUE"));
                        queue.Enqueue((neighbor, distance + 1, "BLUE"));
                    }
                }
            }
        }

        return paths;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int[] shortestAlternatingPaths(int n, int[][] redEdges, int[][] blueEdges) {
        Map<Integer, List<Integer>> redAdj = new HashMap<>();
        Map<Integer, List<Integer>> blueAdj = new HashMap<>();

        for (int[] edge : redEdges) {
            redAdj.computeIfAbsent(edge[0], k -> new ArrayList<>()).add(edge[1]);
        }
        for (int[] edge : blueEdges) {
            blueAdj.computeIfAbsent(edge[0], k -> new ArrayList<>()).add(edge[1]);
        }

        Queue<int[]> queue = new LinkedList<>();
        Set<String> visited = new HashSet<>();
        queue.offer(new int[]{0, 0, -1}); // [node, distance, prevEdge (-1 = NA, 0 = RED, 1 = BLUE)]
        visited.add("0,-1");

        int[] paths = new int[n];
        Arrays.fill(paths, -1);

        while (!queue.isEmpty()) {
            int[] current = queue.poll();
            int node = current[0], distance = current[1], prevEdge = current[2];

            if (paths[node] == -1) {
                paths[node] = distance;
            }

            if (prevEdge != 0 && redAdj.containsKey(node)) {
                for (int neighbor : redAdj.get(node)) {
                    String key = neighbor + ",0";
                    if (!visited.contains(key)) {
                        visited.add(key);
                        queue.offer(new int[]{neighbor, distance + 1, 0});
                    }
                }
            }

            if (prevEdge != 1 && blueAdj.containsKey(node)) {
                for (int neighbor : blueAdj.get(node)) {
                    String key = neighbor + ",1";
                    if (!visited.contains(key)) {
                        visited.add(key);
                        queue.offer(new int[]{neighbor, distance + 1, 1});
                    }
                }
            }
        }

        return paths;
    }
}
```

### Swift

```swift
class Solution {
    func shortestAlternatingPaths(_ n: Int, _ redEdges: [[Int]], _ blueEdges: [[Int]]) -> [Int] {
        var redAdj = [Int: [Int]]()
        var blueAdj = [Int: [Int]]()

        for edge in redEdges {
            redAdj[edge[0], default: []].append(edge[1])
        }

        for edge in blueEdges {
            blueAdj[edge[0], default: []].append(edge[1])
        }

        var queue: [(node: Int, distance: Int, prevEdge: String)] = [(0, 0, "NA")]
        var visited: Set<(Int, String)> = [(0, "NA")]

        var paths = Array(repeating: -1, count: n)

        while !queue.isEmpty {
            let (node, distance, prevEdge) = queue.removeFirst()

            if paths[node] == -1 {
                paths[node] = distance
            }

            if prevEdge != "RED" {
                for neighbor in redAdj[node] ?? [] {
                    let pair = (neighbor, "RED")
                    if !visited.contains(pair) {
                        visited.insert(pair)
                        queue.append((neighbor, distance + 1, "RED"))
                    }
                }
            }

            if prevEdge != "BLUE" {
                for neighbor in blueAdj[node] ?? [] {
                    let pair = (neighbor, "BLUE")
                    if !visited.contains(pair) {
                        visited.insert(pair)
                        queue.append((neighbor, distance + 1, "BLUE"))
                    }
                }
            }
        }

        return paths
    }
}
```

### The End