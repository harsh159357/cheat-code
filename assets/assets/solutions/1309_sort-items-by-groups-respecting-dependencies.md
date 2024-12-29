# Sort Items by Groups Respecting Dependencies

## Problem Statement

You have `n` items, each belonging to one of `m` groups. The groups are numbered from `0` to `m-1`. You are given an array `group` where `group[i]` is the group to which item `i` belongs. If `group[i] == -1`, item `i` does not belong to any group.

Additionally, you are given a `beforeItems` list where `beforeItems[i]` is a list of items that must appear before item `i` in the sorted order.

Return any sorting of the items that satisfies these conditions:

1. The items in each group must appear together.
2. The items in `beforeItems` must appear before the respective item.

If there are multiple valid solutions, return any of them. If no solution exists, return an empty list.

## Input

```text
n = 8
m = 2
group = [-1,0,0,-1,1,1,1,-1]
beforeItems = [[],[6],[5],[6],[3,6],[],[],[]]
```

## Output

```text
[6,3,4,5,1,2,0,7]
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun sortItems(n: Int, m: Int, group: IntArray, beforeItems: List<List<Int>>): IntArray {
        val maxGroup = group.maxOrNull() ?: -1
        val groupMapping = group.mapIndexed { index, grp -> if (grp == -1) index + maxGroup + 1 else grp }.toIntArray()

        val itemGraph = Array(n) { mutableListOf<Int>() }
        val groupGraph = mutableMapOf<Int, MutableList<Int>>()
        val itemIndegree = IntArray(n)
        val groupIndegree = mutableMapOf<Int, Int>().withDefault { 0 }

        for (i in beforeItems.indices) {
            for (j in beforeItems[i]) {
                itemGraph[j].add(i)
                itemIndegree[i]++

                val groupFrom = groupMapping[j]
                val groupTo = groupMapping[i]
                if (groupFrom != groupTo) {
                    groupGraph.computeIfAbsent(groupFrom) { mutableListOf() }.add(groupTo)
                    groupIndegree[groupTo] = groupIndegree.getValue(groupTo) + 1
                }
            }
        }

        val itemOrder = topologicalSort(itemGraph, itemIndegree)
        if (itemOrder.isEmpty()) return intArrayOf()

        val groupOrder = topologicalSort(groupGraph, groupIndegree)
        if (groupOrder.isEmpty()) return intArrayOf()

        val groupedItems = groupOrder.associateWith { mutableListOf<Int>() }
        itemOrder.forEach { groupedItems[groupMapping[it]]!!.add(it) }

        return groupOrder.flatMap { groupedItems[it] ?: emptyList() }.toIntArray()
    }

    private fun topologicalSort(
        graph: Map<Int, MutableList<Int>>,
        indegree: Map<Int, Int>
    ): List<Int> {
        val zeroIndegree = ArrayDeque(indegree.filterValues { it == 0 }.keys)
        val order = mutableListOf<Int>()

        while (zeroIndegree.isNotEmpty()) {
            val node = zeroIndegree.removeFirst()
            order.add(node)

            graph[node]?.forEach {
                val newIndegree = indegree.getValue(it) - 1
                if (newIndegree == 0) zeroIndegree.add(it)
            }
        }

        return if (order.size == indegree.size) order else emptyList()
    }

    private fun topologicalSort(graph: Array<MutableList<Int>>, indegree: IntArray): List<Int> {
        val zeroIndegree = ArrayDeque<Int>()
        val order = mutableListOf<Int>()

        indegree.indices.forEach { if (indegree[it] == 0) zeroIndegree.add(it) }

        while (zeroIndegree.isNotEmpty()) {
            val node = zeroIndegree.removeFirst()
            order.add(node)

            graph[node].forEach {
                indegree[it]--
                if (indegree[it] == 0) zeroIndegree.add(it)
            }
        }

        return if (order.size == graph.size) order else emptyList()
    }
}
```

### Dart

```dart
List<int> sortItems(int n, int m, List<int> group, List<List<int>> beforeItems) {
  int maxGroup = group.reduce((a, b) => a > b ? a : b);
  List<int> groupMapping = group.map((g) => g == -1 ? ++maxGroup : g).toList();

  List<List<int>> itemGraph = List.generate(n, (_) => []);
  Map<int, List<int>> groupGraph = {};
  List<int> itemIndegree = List.filled(n, 0);
  Map<int, int> groupIndegree = {};

  for (int i = 0; i < beforeItems.length; i++) {
    for (int j in beforeItems[i]) {
      itemGraph[j].add(i);
      itemIndegree[i]++;
      int groupFrom = groupMapping[j];
      int groupTo = groupMapping[i];

      if (groupFrom != groupTo) {
        groupGraph.putIfAbsent(groupFrom, () => []).add(groupTo);
        groupIndegree[groupTo] = (groupIndegree[groupTo] ?? 0) + 1;
      }
    }
  }

  List<int> itemOrder = _topologicalSort(itemGraph, itemIndegree);
  if (itemOrder.isEmpty) return [];

  List<int> groupOrder = _topologicalSort(groupGraph, groupIndegree);
  if (groupOrder.isEmpty) return [];

  Map<int, List<int>> groupedItems = {for (var g in groupOrder) g: []};
  for (int item in itemOrder) {
    groupedItems[groupMapping[item]]!.add(item);
  }

  return groupOrder.expand((g) => groupedItems[g] ?? []).toList();
}

List<int> _topologicalSort(List<List<int>> graph, List<int> indegree) {
  Queue<int> zeroIndegree = Queue.of(
      List.generate(indegree.length, (i) => i).where((i) => indegree[i] == 0));
  List<int> order = [];

  while (zeroIndegree.isNotEmpty) {
    int node = zeroIndegree.removeFirst();
    order.add(node);

    for (int neighbor in graph[node]) {
      indegree[neighbor]--;
      if (indegree[neighbor] == 0) zeroIndegree.add(neighbor);
    }
  }

  return order.length == graph.length ? order : [];
}

List<int> _topologicalSort(Map<int, List<int>> graph, Map<int, int> indegree) {
  Queue<int> zeroIndegree = Queue.of(indegree.keys.where((key) => indegree[key] == 0));
  List<int> order = [];

  while (zeroIndegree.isNotEmpty) {
    int node = zeroIndegree.removeFirst();
    order.add(node);

    for (int neighbor in graph[node] ?? []) {
      indegree[neighbor] = indegree[neighbor]! - 1;
      if (indegree[neighbor] == 0) zeroIndegree.add(neighbor);
    }
  }

  return order.length == indegree.length ? order : [];
}
```


### C#

```csharp
using System.Collections.Generic;
using System.Linq;

public class Solution {
    public int[] SortItems(int n, int m, int[] group, IList<IList<int>> beforeItems) {
        int maxGroup = group.Max();
        int[] groupMapping = group.Select((g, i) => g == -1 ? ++maxGroup : g).ToArray();

        var itemGraph = Enumerable.Range(0, n).Select(_ => new List<int>()).ToArray();
        var groupGraph = new Dictionary<int, List<int>>();
        var itemIndegree = new int[n];
        var groupIndegree = new Dictionary<int, int>();

        for (int i = 0; i < beforeItems.Count; i++) {
            foreach (int j in beforeItems[i]) {
                itemGraph[j].Add(i);
                itemIndegree[i]++;

                int groupFrom = groupMapping[j];
                int groupTo = groupMapping[i];

                if (groupFrom != groupTo) {
                    if (!groupGraph.ContainsKey(groupFrom)) groupGraph[groupFrom] = new List<int>();
                    groupGraph[groupFrom].Add(groupTo);
                    groupIndegree[groupTo] = groupIndegree.GetValueOrDefault(groupTo, 0) + 1;
                }
            }
        }

        var itemOrder = TopologicalSort(itemGraph, itemIndegree);
        if (itemOrder == null) return new int[0];

        var groupOrder = TopologicalSort(groupGraph, groupIndegree);
        if (groupOrder == null) return new int[0];

        var groupedItems = groupOrder.ToDictionary(g => g, g => new List<int>());
        foreach (int item in itemOrder) {
            groupedItems[groupMapping[item]].Add(item);
        }

        return groupOrder.SelectMany(g => groupedItems[g]).ToArray();
    }

    private List<int> TopologicalSort(List<int>[] graph, int[] indegree) {
        var zeroIndegree = new Queue<int>(Enumerable.Range(0, indegree.Length).Where(i => indegree[i] == 0));
        var order = new List<int>();

        while (zeroIndegree.Count > 0) {
            int node = zeroIndegree.Dequeue();
            order.Add(node);

            foreach (int neighbor in graph[node]) {
                indegree[neighbor]--;
                if (indegree[neighbor] == 0) zeroIndegree.Enqueue(neighbor);
            }
        }

        return order.Count == graph.Length ? order : null;
    }

    private List<int> TopologicalSort(Dictionary<int, List<int>> graph, Dictionary<int, int> indegree) {
        var zeroIndegree = new Queue<int>(indegree.Where(kv => kv.Value == 0).Select(kv => kv.Key));
        var order = new List<int>();

        while (zeroIndegree.Count > 0) {
            int node = zeroIndegree.Dequeue();
            order.Add(node);

            if (!graph.ContainsKey(node)) continue;
            foreach (int neighbor in graph[node]) {
                indegree[neighbor]--;
                if (indegree[neighbor] == 0) zeroIndegree.Enqueue(neighbor);
            }
        }

        return order.Count == indegree.Count ? order : null;
    }
}
```


### Java

```java
import java.util.*;

class Solution {
    public int[] sortItems(int n, int m, int[] group, List<List<Integer>> beforeItems) {
        int maxGroup = Arrays.stream(group).max().orElse(-1);
        int[] groupMapping = Arrays.stream(group).map(g -> g == -1 ? ++maxGroup : g).toArray();

        List<List<Integer>> itemGraph = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            itemGraph.add(new ArrayList<>());
        }
        Map<Integer, List<Integer>> groupGraph = new HashMap<>();
        int[] itemIndegree = new int[n];
        Map<Integer, Integer> groupIndegree = new HashMap<>();

        for (int i = 0; i < beforeItems.size(); i++) {
            for (int j : beforeItems.get(i)) {
                itemGraph.get(j).add(i);
                itemIndegree[i]++;
                int groupFrom = groupMapping[j];
                int groupTo = groupMapping[i];

                if (groupFrom != groupTo) {
                    groupGraph.computeIfAbsent(groupFrom, k -> new ArrayList<>()).add(groupTo);
                    groupIndegree.put(groupTo, groupIndegree.getOrDefault(groupTo, 0) + 1);
                }
            }
        }

        List<Integer> itemOrder = topologicalSort(itemGraph, itemIndegree);
        if (itemOrder.isEmpty()) return new int[0];

        List<Integer> groupOrder = topologicalSort(groupGraph, groupIndegree);
        if (groupOrder.isEmpty()) return new int[0];

        Map<Integer, List<Integer>> groupedItems = new HashMap<>();
        for (int group : groupOrder) {
            groupedItems.put(group, new ArrayList<>());
        }
        for (int item : itemOrder) {
            groupedItems.get(groupMapping[item]).add(item);
        }

        List<Integer> result = new ArrayList<>();
        for (int group : groupOrder) {
            result.addAll(groupedItems.getOrDefault(group, new ArrayList<>()));
        }
        return result.stream().mapToInt(i -> i).toArray();
    }

    private List<Integer> topologicalSort(List<List<Integer>> graph, int[] indegree) {
        Queue<Integer> zeroIndegree = new LinkedList<>();
        for (int i = 0; i < indegree.length; i++) {
            if (indegree[i] == 0) {
                zeroIndegree.add(i);
            }
        }

        List<Integer> order = new ArrayList<>();
        while (!zeroIndegree.isEmpty()) {
            int node = zeroIndegree.poll();
            order.add(node);

            for (int neighbor : graph.get(node)) {
                indegree[neighbor]--;
                if (indegree[neighbor] == 0) {
                    zeroIndegree.add(neighbor);
                }
            }
        }

        return order.size() == graph.size() ? order : new ArrayList<>();
    }

    private List<Integer> topologicalSort(Map<Integer, List<Integer>> graph, Map<Integer, Integer> indegree) {
        Queue<Integer> zeroIndegree = new LinkedList<>();
        for (Map.Entry<Integer, Integer> entry : indegree.entrySet()) {
            if (entry.getValue() == 0) {
                zeroIndegree.add(entry.getKey());
            }
        }

        List<Integer> order = new ArrayList<>();
        while (!zeroIndegree.isEmpty()) {
            int node = zeroIndegree.poll();
            order.add(node);

            for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                indegree.put(neighbor, indegree.get(neighbor) - 1);
                if (indegree.get(neighbor) == 0) {
                    zeroIndegree.add(neighbor);
                }
            }
        }

        return order.size() == indegree.size() ? order : new ArrayList<>();
    }
}
```


### Swift

```swift
class Solution {
    func sortItems(_ n: Int, _ m: Int, _ group: [Int], _ beforeItems: [[Int]]) -> [Int] {
        var maxGroup = group.max() ?? -1
        var groupMapping = group.enumerated().map { $0.element == -1 ? maxGroup + $0.offset + 1 : $0.element }

        var itemGraph = Array(repeating: [Int](), count: n)
        var groupGraph = [Int: [Int]]()
        var itemIndegree = Array(repeating: 0, count: n)
        var groupIndegree = [Int: Int]()

        for (i, before) in beforeItems.enumerated() {
            for j in before {
                itemGraph[j].append(i)
                itemIndegree[i] += 1
                let groupFrom = groupMapping[j]
                let groupTo = groupMapping[i]

                if groupFrom != groupTo {
                    groupGraph[groupFrom, default: []].append(groupTo)
                    groupIndegree[groupTo, default: 0] += 1
                }
            }
        }

        guard let itemOrder = topologicalSort(itemGraph, itemIndegree),
              let groupOrder = topologicalSort(groupGraph, groupIndegree) else {
            return []
        }

        var groupedItems = [Int: [Int]]()
        for group in groupOrder {
            groupedItems[group] = []
        }
        for item in itemOrder {
            groupedItems[groupMapping[item], default: []].append(item)
        }

        return groupOrder.flatMap { groupedItems[$0] ?? [] }
    }

    private func topologicalSort(_ graph: [[Int]], _ indegree: [Int]) -> [Int]? {
        var zeroIndegree = Array(indegree.enumerated().filter { $0.element == 0 }.map { $0.offset })
        var order = [Int]()

        while !zeroIndegree.isEmpty {
            let node = zeroIndegree.removeFirst()
            order.append(node)

            for neighbor in graph[node] {
                indegree[neighbor] -= 1
                if indegree[neighbor] == 0 {
                    zeroIndegree.append(neighbor)
                }
            }
        }

        return order.count == graph.count ? order : nil
    }

    private func topologicalSort(_ graph: [Int: [Int]], _ indegree: [Int: Int]) -> [Int]? {
        var zeroIndegree = Array(indegree.filter { $0.value == 0 }.keys)
        var order = [Int]()

        while !zeroIndegree.isEmpty {
            let node = zeroIndegree.removeFirst()
            order.append(node)

            for neighbor in graph[node, default: []] {
                indegree[neighbor]! -= 1
                if indegree[neighbor]! == 0 {
                    zeroIndegree.append(neighbor)
                }
            }
        }

        return order.count == indegree.count ? order : nil
    }
}
```


### The End