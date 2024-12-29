# Largest Color Value in a Directed Graph

## Problem Statement

You are given a directed graph of `n` nodes numbered from `0` to `n-1`, represented by a string `colors` where `colors[i]` is a lowercase English letter representing the color of the `i-th` node. You are also given a 2D array `edges` where `edges[j] = [aj, bj]` indicates a directed edge from node `aj` to node `bj`.

Return the largest color value in any valid path in the graph. If the graph contains a cycle, return `-1`.

The color value of a path is the maximum number of nodes with the same color in the path.

## Input

```text
colors = "abaca"
edges = [[0,1],[0,2],[2,3],[3,4]]
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun largestPathValue(colors: String, edges: Array<IntArray>): Int {
        val connections = Array(colors.length) { mutableListOf<Int>() }
        val inCounts = IntArray(colors.length)

        for (edge in edges) {
            connections[edge[0]].add(edge[1])
            inCounts[edge[1]]++
        }

        val queue = LinkedList<Int>()
        val counts = Array(colors.length) { IntArray(26) }

        // Add all nodes with in-degree zero to the queue
        for (i in inCounts.indices) {
            if (inCounts[i] == 0) {
                queue.offer(i)
            }
        }

        var max = 0
        var nodesSeen = 0

        while (queue.isNotEmpty()) {
            val node = queue.poll()
            max = maxOf(max, ++counts[node][colors[node] - 'a'])
            nodesSeen++

            for (neighbor in connections[node]) {
                for (c in 0 until 26) {
                    counts[neighbor][c] = maxOf(counts[neighbor][c], counts[node][c])
                }
                inCounts[neighbor]--
                if (inCounts[neighbor] == 0) {
                    queue.offer(neighbor)
                }
            }
        }

        return if (nodesSeen == colors.length) max else -1
    }
}

fun main() {
    val colors = "abaca"
    val edges = arrayOf(
        intArrayOf(0, 1),
        intArrayOf(0, 2),
        intArrayOf(2, 3),
        intArrayOf(3, 4)
    )
    println(Solution().largestPathValue(colors, edges)) // Output: 3
}
```

### Dart

```dart
int largestPathValue(String colors, List<List<int>> edges) {
  int n = colors.length;
  List<List<int>> graph = List.generate(n, (_) => []);
  List<int> inDegree = List.filled(n, 0);
  List<List<int>> colorCount = List.generate(n, (_) => List.filled(26, 0));
  
  for (var edge in edges) {
    graph[edge[0]].add(edge[1]);
    inDegree[edge[1]]++;
  }
  
  Queue<int> queue = Queue();
  for (int i = 0; i < n; i++) {
    if (inDegree[i] == 0) queue.add(i);
  }
  
  int maxCount = 0, nodesSeen = 0;
  
  while (queue.isNotEmpty) {
    int node = queue.removeFirst();
    nodesSeen++;
    colorCount[node][colors.codeUnitAt(node) - 'a'.codeUnitAt(0)]++;
    maxCount = max(maxCount, colorCount[node][colors.codeUnitAt(node) - 'a'.codeUnitAt(0)]);
    
    for (int neighbor in graph[node]) {
      for (int i = 0; i < 26; i++) {
        colorCount[neighbor][i] = max(colorCount[neighbor][i], colorCount[node][i]);
      }
      inDegree[neighbor]--;
      if (inDegree[neighbor] == 0) queue.add(neighbor);
    }
  }
  
  return nodesSeen == n ? maxCount : -1;
}

void main() {
  String colors = "abaca";
  List<List<int>> edges = [
    [0, 1],
    [0, 2],
    [2, 3],
    [3, 4]
  ];
  print(largestPathValue(colors, edges)); // Output: 3
}
```

### The End