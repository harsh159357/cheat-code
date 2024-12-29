# Time Needed to Inform All Employees

## Problem Statement

A company has `n` employees, each with a unique ID from `0` to `n-1`. The head of the company has an ID of `headID`. Each employee has a direct manager given by the `manager` array, where `manager[i]` is the direct manager of the `i`th employee. The value `manager[i] == -1` indicates that the `i`th employee is the head of the company.

The time it takes to inform an employee and their subordinates is given by the `informTime` array. Return the total time required to inform all employees.

## Input

```text
n = 6
headID = 2
manager = [2, 2, -1, 2, 2, 2]
informTime = [0, 0, 1, 0, 0, 0]
```

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun numOfMinutes(n: Int, headID: Int, manager: IntArray, informTime: IntArray): Int {
        val graph = HashMap<Int, MutableList<Int>>()
        for (i in manager.indices) {
            if (!graph.containsKey(manager[i])) {
                graph[manager[i]] = mutableListOf()
            }
            graph[manager[i]]!!.add(i)
        }
        return dfs(headID, graph, informTime)
    }

    private fun dfs(manager: Int, graph: Map<Int, List<Int>>, informTime: IntArray): Int {
        if (!graph.containsKey(manager)) return 0
        var maxTime = 0
        for (subordinate in graph[manager]!!) {
            maxTime = maxOf(maxTime, dfs(subordinate, graph, informTime))
        }
        return maxTime + informTime[manager]
    }
}
```

### Dart

```dart
int numOfMinutes(int n, int headID, List<int> manager, List<int> informTime) {
  Map<int, List<int>> graph = {};

  for (int i = 0; i < manager.length; i++) {
    graph.putIfAbsent(manager[i], () => []).add(i);
  }

  int dfs(int manager) {
    if (!graph.containsKey(manager)) return 0;

    int maxTime = 0;
    for (int subordinate in graph[manager]!) {
      maxTime = max(maxTime, dfs(subordinate));
    }

    return maxTime + informTime[manager];
  }

  return dfs(headID);
}
```

### C#

```csharp
public class Solution {
    public int NumOfMinutes(int n, int headID, int[] manager, int[] informTime) {
        Dictionary<int, List<int>> graph = new Dictionary<int, List<int>>();

        for (int i = 0; i < manager.Length; i++) {
            if (!graph.ContainsKey(manager[i])) {
                graph[manager[i]] = new List<int>();
            }
            graph[manager[i]].Add(i);
        }

        int Dfs(int manager) {
            if (!graph.ContainsKey(manager)) return 0;

            int maxTime = 0;
            foreach (int subordinate in graph[manager]) {
                maxTime = Math.Max(maxTime, Dfs(subordinate));
            }

            return maxTime + informTime[manager];
        }

        return Dfs(headID);
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int numOfMinutes(int n, int headID, int[] manager, int[] informTime) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        for (int i = 0; i < manager.length; i++) {
            graph.computeIfAbsent(manager[i], k -> new ArrayList<>()).add(i);
        }
        return dfs(headID, graph, informTime);
    }

    private int dfs(int manager, Map<Integer, List<Integer>> graph, int[] informTime) {
        if (!graph.containsKey(manager)) return 0;

        int maxTime = 0;
        for (int subordinate : graph.get(manager)) {
            maxTime = Math.max(maxTime, dfs(subordinate, graph, informTime));
        }

        return maxTime + informTime[manager];
    }
}
```

### Swift

```swift
class Solution {
    func numOfMinutes(_ n: Int, _ headID: Int, _ manager: [Int], _ informTime: [Int]) -> Int {
        var graph = [Int: [Int]]()

        for i in 0..<manager.count {
            graph[manager[i], default: []].append(i)
        }

        func dfs(_ manager: Int) -> Int {
            if !graph.keys.contains(manager) { return 0 }

            var maxTime = 0
            for subordinate in graph[manager]! {
                maxTime = max(maxTime, dfs(subordinate))
            }

            return maxTime + informTime[manager]
        }

        return dfs(headID)
    }
}
```

### The End