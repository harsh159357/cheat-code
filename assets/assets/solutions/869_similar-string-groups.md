# Similar String Groups

## Problem Statement

You are given an array of strings `strs`. Two strings are considered similar if they have the same length and their characters differ by at most two positions. A string `A` is similar to string `B` if one of the following is true:
1. `A` and `B` are directly similar.
2. `A` is similar to another string `C`, and `C` is similar to `B`.

Return the number of groups formed by the strings.

## Input

```text
strs = ["tars", "rats", "arts", "star"]
```

## Output

```text
2
```


## Solutions

### Dart

```dart
int numSimilarGroups(List<String> strs) {
  Set<String> visited = {};
  Map<String, List<String>> graph = {};

  for (String str in strs) {
    graph[str] = [];
  }

  for (int i = 0; i < strs.length; i++) {
    for (int j = i + 1; j < strs.length; j++) {
      if (areSimilar(strs[i], strs[j])) {
        graph[strs[i]]!.add(strs[j]);
        graph[strs[j]]!.add(strs[i]);
      }
    }
  }

  int numGroups = 0;

  void dfs(String str) {
    visited.add(str);
    for (String neighbor in graph[str]!) {
      if (!visited.contains(neighbor)) {
        dfs(neighbor);
      }
    }
  }

  for (String str in strs) {
    if (!visited.contains(str)) {
      dfs(str);
      numGroups++;
    }
  }

  return numGroups;
}

bool areSimilar(String a, String b) {
  int diffCount = 0;
  for (int i = 0; i < a.length; i++) {
    if (a[i] != b[i] && ++diffCount > 2) {
      return false;
    }
  }
  return true;
}
```

### C#

```csharp
public class Solution {
    public int NumSimilarGroups(string[] strs) {
        var visited = new HashSet<string>();
        var graph = new Dictionary<string, List<string>>();

        foreach (var str in strs) {
            graph[str] = new List<string>();
        }

        for (int i = 0; i < strs.Length; i++) {
            for (int j = i + 1; j < strs.Length; j++) {
                if (AreSimilar(strs[i], strs[j])) {
                    graph[strs[i]].Add(strs[j]);
                    graph[strs[j]].Add(strs[i]);
                }
            }
        }

        int numGroups = 0;

        void Dfs(string str) {
            visited.Add(str);
            foreach (var neighbor in graph[str]) {
                if (!visited.Contains(neighbor)) {
                    Dfs(neighbor);
                }
            }
        }

        foreach (var str in strs) {
            if (visited.Add(str)) {
                Dfs(str);
                numGroups++;
            }
        }

        return numGroups;
    }

    private bool AreSimilar(string a, string b) {
        int diffCount = 0;
        for (int i = 0; i < a.Length; i++) {
            if (a[i] != b[i] && ++diffCount > 2) {
                return false;
            }
        }
        return true;
    }
}
```

### Java

```java
class Solution {
    public int numSimilarGroups(String[] strs) {
        Set<String> visited = new HashSet<>();
        Map<String, List<String>> graph = new HashMap<>();

        for (String str : strs) {
            graph.put(str, new ArrayList<>());
        }

        for (int i = 0; i < strs.length; i++) {
            for (int j = i + 1; j < strs.length; j++) {
                if (areSimilar(strs[i], strs[j])) {
                    graph.get(strs[i]).add(strs[j]);
                    graph.get(strs[j]).add(strs[i]);
                }
            }
        }

        int numGroups = 0;

        for (String str : strs) {
            if (visited.add(str)) {
                dfs(str, graph, visited);
                numGroups++;
            }
        }

        return numGroups;
    }

    private void dfs(String str, Map<String, List<String>> graph, Set<String> visited) {
        for (String neighbor : graph.get(str)) {
            if (visited.add(neighbor)) {
                dfs(neighbor, graph, visited);
            }
        }
    }

    private boolean areSimilar(String a, String b) {
        int diffCount = 0;
        for (int i = 0; i < a.length(); i++) {
            if (a.charAt(i) != b.charAt(i) && ++diffCount > 2) {
                return false;
            }
        }
        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun numSimilarGroups(strs: Array<String>): Int {
        val visited = mutableSetOf<String>()
        var numGroups = 0

        val graph = mutableMapOf<String, MutableList<String>>()
        for (str in strs) {
            graph[str] = mutableListOf()
        }

        for (i in strs.indices) {
            for (j in i + 1 until strs.size) {
                if (areSimilar(strs[i], strs[j])) {
                    graph[strs[i]]!!.add(strs[j])
                    graph[strs[j]]!!.add(strs[i])
                }
            }
        }

        for (str in strs) {
            if (visited.add(str)) {
                dfs(str, graph, visited)
                numGroups++
            }
        }

        return numGroups
    }

    private fun dfs(str: String, graph: Map<String, List<String>>, visited: MutableSet<String>) {
        for (neighbor in graph[str]!!) {
            if (visited.add(neighbor)) {
                dfs(neighbor, graph, visited)
            }
        }
    }

    private fun areSimilar(a: String, b: String): Boolean {
        var diffCount = 0
        for (i in a.indices) {
            if (a[i] != b[i] && ++diffCount > 2) {
                return false
            }
        }
        return true
    }
}
```

### Swift

```swift
class Solution {
    func numSimilarGroups(_ strs: [String]) -> Int {
        var visited = Set<String>()
        var graph = [String: [String]]()

        for str in strs {
            graph[str] = []
        }

        for i in 0..<strs.count {
            for j in i + 1..<strs.count {
                if areSimilar(strs[i], strs[j]) {
                    graph[strs[i]]!.append(strs[j])
                    graph[strs[j]]!.append(strs[i])
                }
            }
        }

        var numGroups = 0

        func dfs(_ str: String) {
            visited.insert(str)
            for neighbor in graph[str]! {
                if !visited.contains(neighbor) {
                    dfs(neighbor)
                }
            }
        }

        for str in strs {
            if !visited.contains(str) {
                dfs(str)
                numGroups += 1
            }
        }

        return numGroups
    }

    private func areSimilar(_ a: String, _ b: String) -> Bool {
        var diffCount = 0
        let aArray = Array(a)
        let bArray = Array(b)

        for i in 0..<aArray.count {
            if aArray[i] != bArray[i] {
                diffCount += 1
                if diffCount > 2 {
                    return false
                }
            }
        }
        return true
    }
}
```

### The End