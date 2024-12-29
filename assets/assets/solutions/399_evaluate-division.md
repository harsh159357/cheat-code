# Evaluate Division

## Problem Statement

You are given a list of equations where `equations[i] = [Ai, Bi]` represents the equation `Ai / Bi = values[i]`. Each equation consists of a variable pair and their corresponding value.

You are also given some queries, where `queries[j] = [Cj, Dj]` represents the query `Cj / Dj`. Return the answers to all queries. If the division operation cannot be performed, return `-1.0`.

## Input

```text
equations = [["a", "b"], ["b", "c"]]
values = [2.0, 3.0]
queries = [["a", "c"], ["b", "a"], ["a", "e"], ["a", "a"], ["x", "x"]]
```

## Output

```text
[6.0, 0.5, -1.0, 1.0, -1.0]
```

## Solutions

### Dart

```dart
List<double> calcEquation(
    List<List<String>> equations,
    List<double> values,
    List<List<String>> queries) {
  final graph = <String, Map<String, double>>{};

  // Populate the graph
  for (int i = 0; i < equations.length; i++) {
    final a = equations[i][0], b = equations[i][1];
    final value = values[i];
    graph.putIfAbsent(a, () => {})[b] = value;
    graph.putIfAbsent(b, () => {})[a] = 1 / value;
  }

  double? dfs(String x, String y, Set<String> visited) {
    if (!graph.containsKey(x) || !graph.containsKey(y)) return null;
    if (x == y) return 1.0;
    visited.add(x);
    for (final neighbor in graph[x]!.keys) {
      if (visited.contains(neighbor)) continue;
      final result = dfs(neighbor, y, visited);
      if (result != null) return graph[x]![neighbor]! * result;
    }
    return null;
  }

  return queries.map((query) {
    final x = query[0], y = query[1];
    return dfs(x, y, <String>{}) ?? -1.0;
  }).toList();
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public double[] CalcEquation(IList<IList<string>> equations, double[] values, IList<IList<string>> queries) {
        var graph = new Dictionary<string, Dictionary<string, double>>();

        // Populate the graph
        for (int i = 0; i < equations.Count; i++) {
            var a = equations[i][0];
            var b = equations[i][1];
            var value = values[i];

            if (!graph.ContainsKey(a)) graph[a] = new Dictionary<string, double>();
            if (!graph.ContainsKey(b)) graph[b] = new Dictionary<string, double>();

            graph[a][b] = value;
            graph[b][a] = 1 / value;
        }

        double? Dfs(string x, string y, HashSet<string> visited) {
            if (!graph.ContainsKey(x) || !graph.ContainsKey(y)) return null;
            if (x == y) return 1.0;

            visited.Add(x);

            foreach (var neighbor in graph[x]) {
                if (visited.Contains(neighbor.Key)) continue;
                var result = Dfs(neighbor.Key, y, visited);
                if (result != null) return neighbor.Value * result;
            }
            return null;
        }

        var results = new double[queries.Count];
        for (int i = 0; i < queries.Count; i++) {
            var x = queries[i][0];
            var y = queries[i][1];
            results[i] = Dfs(x, y, new HashSet<string>()) ?? -1.0;
        }

        return results;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public double[] calcEquation(List<List<String>> equations, double[] values, List<List<String>> queries) {
        Map<String, Map<String, Double>> graph = new HashMap<>();

        // Populate the graph
        for (int i = 0; i < equations.size(); i++) {
            String a = equations.get(i).get(0);
            String b = equations.get(i).get(1);
            double value = values[i];
            graph.putIfAbsent(a, new HashMap<>());
            graph.putIfAbsent(b, new HashMap<>());
            graph.get(a).put(b, value);
            graph.get(b).put(a, 1.0 / value);
        }

        double dfs(String x, String y, Set<String> visited) {
            if (!graph.containsKey(x) || !graph.containsKey(y)) return -1.0;
            if (x.equals(y)) return 1.0;

            visited.add(x);
            for (Map.Entry<String, Double> neighbor : graph.get(x).entrySet()) {
                if (visited.contains(neighbor.getKey())) continue;
                double result = dfs(neighbor.getKey(), y, visited);
                if (result != -1.0) return neighbor.getValue() * result;
            }
            return -1.0;
        }

        double[] results = new double[queries.size()];
        for (int i = 0; i < queries.size(); i++) {
            String x = queries.get(i).get(0);
            String y = queries.get(i).get(1);
            results[i] = dfs(x, y, new HashSet<>());
        }

        return results;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun calcEquation(
        equations: List<List<String>>,
        values: DoubleArray,
        queries: List<List<String>>
    ): DoubleArray {
        val graph = mutableMapOf<String, MutableMap<String, Double>>()

        // Populate the graph
        for (i in equations.indices) {
            val (a, b) = equations[i]
            val value = values[i]
            graph.getOrPut(a) { mutableMapOf() }[b] = value
            graph.getOrPut(b) { mutableMapOf() }[a] = 1 / value
        }

        fun dfs(x: String, y: String, visited: MutableSet<String>): Double? {
            if (x !in graph || y !in graph) return null
            if (x == y) return 1.0
            visited.add(x)
            for ((neighbor, value) in graph[x]!!) {
                if (neighbor in visited) continue
                val result = dfs(neighbor, y, visited)
                if (result != null) return value * result
            }
            return null
        }

        val results = DoubleArray(queries.size)
        for (i in queries.indices) {
            val (x, y) = queries[i]
            results[i] = dfs(x, y, mutableSetOf()) ?: -1.0
        }
        return results
    }
}
```

### Swift

```swift
class Solution {
    func calcEquation(_ equations: [[String]], _ values: [Double], _ queries: [[String]]) -> [Double] {
        var graph = [String: [String: Double]]()

        // Populate the graph
        for i in 0..<equations.count {
            let a = equations[i][0]
            let b = equations[i][1]
            let value = values[i]
            graph[a, default: [:]][b] = value
            graph[b, default: [:]][a] = 1.0 / value
        }

        func dfs(_ x: String, _ y: String, _ visited: inout Set<String>) -> Double? {
            if graph[x] == nil || graph[y] == nil { return nil }
            if x == y { return 1.0 }
            visited.insert(x)
            for (neighbor, value) in graph[x]! {
                if visited.contains(neighbor) { continue }
                if let result = dfs(neighbor, y, &visited) {
                    return value * result
                }
            }
            return nil
        }

        return queries.map { query in
            var visited = Set<String>()
            return dfs(query[0], query[1], &visited) ?? -1.0
        }
    }
}
```

### The End