# Maximal Network Rank

## Problem Statement

You are given an integer `n`, the number of cities, and an array `roads` where `roads[i] = [a, b]` represents a bidirectional road between cities `a` and `b`. A city's network rank is the total number of roads connected to it. The network rank of two cities is the total number of roads connected to either city, excluding any road directly connecting the two cities.

Return the **maximal network rank** of any two different cities.

## Input

```text
n = 4
roads = [[0,1],[0,3],[1,2],[1,3]]
```

## Output

```text
4
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun maximalNetworkRank(n: Int, roads: Array<IntArray>): Int {
        val connections = Array(n) { mutableSetOf<Int>() }

        // Build adjacency sets for each city
        for (road in roads) {
            connections[road[0]].add(road[1])
            connections[road[1]].add(road[0])
        }

        var maxRank = 0

        // Calculate network ranks for each pair of cities
        for (i in 0 until n) {
            for (j in i + 1 until n) {
                val rank = connections[i].size + connections[j].size -
                           if (connections[i].contains(j)) 1 else 0
                maxRank = maxOf(maxRank, rank)
            }
        }

        return maxRank
    }
}

fun main() {
    val n = 4
    val roads = arrayOf(
        intArrayOf(0, 1),
        intArrayOf(0, 3),
        intArrayOf(1, 2),
        intArrayOf(1, 3)
    )
    println(Solution().maximalNetworkRank(n, roads)) // Output: 4
}
```

### Dart

```dart
int maximalNetworkRank(int n, List<List<int>> roads) {
  List<Set<int>> connections = List.generate(n, (_) => <int>{});

  // Build adjacency sets for each city
  for (var road in roads) {
    connections[road[0]].add(road[1]);
    connections[road[1]].add(road[0]);
  }

  int maxRank = 0;

  // Calculate network ranks for each pair of cities
  for (int i = 0; i < n; i++) {
    for (int j = i + 1; j < n; j++) {
      int rank = connections[i].length + connections[j].length -
          (connections[i].contains(j) ? 1 : 0);
      maxRank = max(maxRank, rank);
    }
  }

  return maxRank;
}
```

### C#

```csharp
public class Solution {
    public int MaximalNetworkRank(int n, int[][] roads) {
        var connections = new HashSet<int>[n];
        for (int i = 0; i < n; i++) {
            connections[i] = new HashSet<int>();
        }

        // Build adjacency sets for each city
        foreach (var road in roads) {
            connections[road[0]].Add(road[1]);
            connections[road[1]].Add(road[0]);
        }

        int maxRank = 0;

        // Calculate network ranks for each pair of cities
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int rank = connections[i].Count + connections[j].Count -
                           (connections[i].Contains(j) ? 1 : 0);
                maxRank = Math.Max(maxRank, rank);
            }
        }

        return maxRank;
    }
}
```

### Java

```java
class Solution {
    public int maximalNetworkRank(int n, int[][] roads) {
        Set<Integer>[] connections = new Set[n];
        for (int i = 0; i < n; i++) {
            connections[i] = new HashSet<>();
        }

        // Build adjacency sets for each city
        for (int[] road : roads) {
            connections[road[0]].add(road[1]);
            connections[road[1]].add(road[0]);
        }

        int maxRank = 0;

        // Calculate network ranks for each pair of cities
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int rank = connections[i].size() + connections[j].size() -
                           (connections[i].contains(j) ? 1 : 0);
                maxRank = Math.max(maxRank, rank);
            }
        }

        return maxRank;
    }
}
```

### Swift

```swift
class Solution {
    func maximalNetworkRank(_ n: Int, _ roads: [[Int]]) -> Int {
        var connections = Array(repeating: Set<Int>(), count: n)

        // Build adjacency sets for each city
        for road in roads {
            connections[road[0]].insert(road[1])
            connections[road[1]].insert(road[0])
        }

        var maxRank = 0

        // Calculate network ranks for each pair of cities
        for i in 0..<n {
            for j in i + 1..<n {
                let rank = connections[i].count + connections[j].count -
                           (connections[i].contains(j) ? 1 : 0)
                maxRank = max(maxRank, rank)
            }
        }

        return maxRank
    }
}
```

### The End