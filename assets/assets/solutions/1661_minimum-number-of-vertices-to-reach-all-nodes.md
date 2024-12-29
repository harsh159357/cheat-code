# Minimum Number of Vertices to Reach All Nodes

## Problem Statement

Given a directed acyclic graph with `n` nodes numbered from `0` to `n-1`, and a list of `edges` where `edges[i] = [from_i, to_i]` represents a directed edge from node `from_i` to node `to_i`, return a list of the smallest set of vertices such that every node in the graph is reachable from at least one of these vertices.

## Input

```text
n = 6
edges = [[0, 1], [0, 2], [2, 5], [3, 4], [4, 2]]
```

## Output

```text
[0, 3]
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findSmallestSetOfVertices(n: Int, edges: List<List<Int>>): List<Int> {
        val destination = HashSet<Int>()

        // Add destination vertices to the set
        for (edge in edges) {
            destination.add(edge[1])
        }

        // Nodes not in the destination set are the ones without incoming edges
        val result = mutableListOf<Int>()
        for (i in 0 until n) {
            if (!destination.contains(i)) {
                result.add(i)
            }
        }

        return result
    }
}

fun main() {
    val solution = Solution()

    // Example usage
    val n = 6
    val edges = listOf(
        listOf(0, 1),
        listOf(0, 2),
        listOf(2, 5),
        listOf(3, 4),
        listOf(4, 2)
    )
    val result = solution.findSmallestSetOfVertices(n, edges)
    println("Minimum vertices to reach all nodes: $result")
}
```

### Dart

```dart
List<int> findSmallestSetOfVertices(int n, List<List<int>> edges) {
  Set<int> destination = {};

  for (var edge in edges) {
    destination.add(edge[1]);
  }

  List<int> result = [];
  for (int i = 0; i < n; i++) {
    if (!destination.contains(i)) {
      result.add(i);
    }
  }

  return result;
}

void main() {
  int n = 6;
  List<List<int>> edges = [
    [0, 1],
    [0, 2],
    [2, 5],
    [3, 4],
    [4, 2]
  ];
  print("Minimum vertices to reach all nodes: ${findSmallestSetOfVertices(n, edges)}");
}
```

### C#

```csharp
public class Solution {
    public IList<int> FindSmallestSetOfVertices(int n, IList<IList<int>> edges) {
        HashSet<int> destination = new HashSet<int>();

        foreach (var edge in edges) {
            destination.Add(edge[1]);
        }

        List<int> result = new List<int>();
        for (int i = 0; i < n; i++) {
            if (!destination.Contains(i)) {
                result.Add(i);
            }
        }

        return result;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public List<Integer> findSmallestSetOfVertices(int n, List<List<Integer>> edges) {
        Set<Integer> destination = new HashSet<>();

        for (List<Integer> edge : edges) {
            destination.add(edge.get(1));
        }

        List<Integer> result = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            if (!destination.contains(i)) {
                result.add(i);
            }
        }

        return result;
    }
}
```

### Swift

```swift
class Solution {
    func findSmallestSetOfVertices(_ n: Int, _ edges: [[Int]]) -> [Int] {
        var destination = Set<Int>()

        for edge in edges {
            destination.insert(edge[1])
        }

        var result = [Int]()
        for i in 0..<n {
            if !destination.contains(i) {
                result.append(i)
            }
        }

        return result
    }
}
```

### The End