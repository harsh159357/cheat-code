# All Paths From Source to Target

## Problem Statement

Given a directed acyclic graph (DAG) of `n` nodes labeled from `0` to `n-1`, find all possible paths from node `0` to node `n-1`. The graph is given as a list where `graph[i]` is a list of all nodes you can visit from node `i`.

## Input

```text
graph = [[1, 2], [3], [3], []]
```

## Output

```text
[[0, 1, 3], [0, 2, 3]]
```

## Solutions

### Dart

```dart
List<List<int>> allPathsSourceTarget(List<List<int>> graph) {
  List<List<int>> result = [];
  List<int> path = [0];

  void dfs(int node) {
    if (node == graph.length - 1) {
      result.add(List.from(path));
      return;
    }
    for (int nextNode in graph[node]) {
      path.add(nextNode);
      dfs(nextNode);
      path.removeLast();
    }
  }

  dfs(0);
  return result;
}
```

### C#

```csharp
public class Solution {
    public IList<IList<int>> AllPathsSourceTarget(int[][] graph) {
        var result = new List<IList<int>>();
        var path = new List<int> { 0 };

        void Dfs(int node) {
            if (node == graph.Length - 1) {
                result.Add(new List<int>(path));
                return;
            }
            foreach (int nextNode in graph[node]) {
                path.Add(nextNode);
                Dfs(nextNode);
                path.RemoveAt(path.Count - 1);
            }
        }

        Dfs(0);
        return result;
    }
}
```

### Java

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> path = new ArrayList<>();
        path.add(0);
        dfs(graph, 0, path, result);
        return result;
    }

    private void dfs(int[][] graph, int node, List<Integer> path, List<List<Integer>> result) {
        if (node == graph.length - 1) {
            result.add(new ArrayList<>(path));
            return;
        }
        for (int nextNode : graph[node]) {
            path.add(nextNode);
            dfs(graph, nextNode, path, result);
            path.remove(path.size() - 1);
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun allPathsSourceTarget(graph: Array<IntArray>): List<List<Int>> {
        val result = mutableListOf<List<Int>>()
        val path = mutableListOf(0)
        dfs(graph, 0, path, result)
        return result
    }

    private fun dfs(graph: Array<IntArray>, node: Int, path: MutableList<Int>, result: MutableList<List<Int>>) {
        if (node == graph.size - 1) {
            result.add(path.toList())
            return
        }
        for (nextNode in graph[node]) {
            path.add(nextNode)
            dfs(graph, nextNode, path, result)
            path.removeAt(path.size - 1)
        }
    }
}
```

### Swift

```swift
class Solution {
    func allPathsSourceTarget(_ graph: [[Int]]) -> [[Int]] {
        var result = [[Int]]()
        var path = [0]

        func dfs(_ node: Int) {
            if node == graph.count - 1 {
                result.append(path)
                return
            }
            for nextNode in graph[node] {
                path.append(nextNode)
                dfs(nextNode)
                path.removeLast()
            }
        }

        dfs(0)
        return result
    }
}
```


### The End