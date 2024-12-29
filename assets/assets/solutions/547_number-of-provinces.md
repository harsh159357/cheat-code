# Number of Provinces

## Problem Statement

There are `n` cities connected by some number of roads. The `isConnected` array is a `n x n` matrix where `isConnected[i][j] = 1` if city `i` and city `j` are directly connected, and `isConnected[i][j] = 0` otherwise.

A province is a group of directly or indirectly connected cities. Return the total number of provinces.

## Input

```text
isConnected = [
    [1, 1, 0],
    [1, 1, 0],
    [0, 0, 1]
]
```

## Output

```text
2
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findCircleNum(isConnected: Array<IntArray>): Int {
        val visited = BooleanArray(isConnected.size)
        var provinces = 0
        for (i in isConnected.indices) {
            if (!visited[i]) {
                provinces++
                dfs(isConnected, i, visited)
            }
        }
        return provinces
    }

    private fun dfs(isConnected: Array<IntArray>, city: Int, visited: BooleanArray) {
        visited[city] = true
        for (adjCity in isConnected[city].indices) {
            if (isConnected[city][adjCity] == 1 && !visited[adjCity]) {
                dfs(isConnected, adjCity, visited)
            }
        }
    }
}

fun main() {
    val isConnected = arrayOf(
        intArrayOf(1, 1, 0),
        intArrayOf(1, 1, 0),
        intArrayOf(0, 0, 1)
    )
    val solution = Solution()
    println("Number of Provinces: ${solution.findCircleNum(isConnected)}") // Output: 2
}
```

### Dart

```dart
int findCircleNum(List<List<int>> isConnected) {
  int n = isConnected.length;
  List<bool> visited = List.filled(n, false);
  int provinces = 0;

  void dfs(int city) {
    visited[city] = true;
    for (int adjCity = 0; adjCity < n; adjCity++) {
      if (isConnected[city][adjCity] == 1 && !visited[adjCity]) {
        dfs(adjCity);
      }
    }
  }

  for (int i = 0; i < n; i++) {
    if (!visited[i]) {
      provinces++;
      dfs(i);
    }
  }

  return provinces;
}

void main() {
  List<List<int>> isConnected = [
    [1, 1, 0],
    [1, 1, 0],
    [0, 0, 1]
  ];
  print("Number of Provinces: ${findCircleNum(isConnected)}"); // Output: 2
}
```

### Java

```java
class Solution {
    public int findCircleNum(int[][] isConnected) {
        boolean[] visited = new boolean[isConnected.length];
        int provinces = 0;

        for (int i = 0; i < isConnected.length; i++) {
            if (!visited[i]) {
                provinces++;
                dfs(isConnected, i, visited);
            }
        }

        return provinces;
    }

    private void dfs(int[][] isConnected, int city, boolean[] visited) {
        visited[city] = true;
        for (int adjCity = 0; adjCity < isConnected.length; adjCity++) {
            if (isConnected[city][adjCity] == 1 && !visited[adjCity]) {
                dfs(isConnected, adjCity, visited);
            }
        }
    }
}
```

### C#

```csharp
public class Solution {
    public int FindCircleNum(int[][] isConnected) {
        bool[] visited = new bool[isConnected.Length];
        int provinces = 0;

        for (int i = 0; i < isConnected.Length; i++) {
            if (!visited[i]) {
                provinces++;
                Dfs(isConnected, i, visited);
            }
        }

        return provinces;
    }

    private void Dfs(int[][] isConnected, int city, bool[] visited) {
        visited[city] = true;
        for (int adjCity = 0; adjCity < isConnected.Length; adjCity++) {
            if (isConnected[city][adjCity] == 1 && !visited[adjCity]) {
                Dfs(isConnected, adjCity, visited);
            }
        }
    }
}
```

### Swift

```swift
class Solution {
    func findCircleNum(_ isConnected: [[Int]]) -> Int {
        var visited = [Bool](repeating: false, count: isConnected.count)
        var provinces = 0

        func dfs(_ city: Int) {
            visited[city] = true
            for adjCity in 0..<isConnected.count {
                if isConnected[city][adjCity] == 1 && !visited[adjCity] {
                    dfs(adjCity)
                }
            }
        }

        for i in 0..<isConnected.count {
            if !visited[i] {
                provinces += 1
                dfs(i)
            }
        }

        return provinces
    }
}

// Example usage
let isConnected = [
    [1, 1, 0],
    [1, 1, 0],
    [0, 0, 1]
]
let solution = Solution()
print("Number of Provinces: \(solution.findCircleNum(isConnected))") // Output: 2
```

### The End