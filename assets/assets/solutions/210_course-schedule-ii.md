# Course Schedule II

## Problem Statement

There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. Some courses may have prerequisites, for example, to take course `0` you have to first take course `1`, which is expressed as a pair: `[0, 1]`.

Given the total number of courses and a list of prerequisite pairs, return the ordering of courses you should take to finish all courses. If it is impossible to finish all courses, return an empty array.

## Input

```text
numCourses = 4
prerequisites = [[1,0],[2,0],[3,1],[3,2]]
```

## Output

```text
[0,2,1,3]
```

## Solutions

### Dart

```dart
List<int> findOrder(int numCourses, List<List<int>> prerequisites) {
  List<List<int>> preReq = List.generate(numCourses, (_) => []);
  prerequisites.forEach((pair) => preReq[pair[0]].add(pair[1]));

  Set<int> visited = {};
  Set<int> cycle = {};
  List<int> result = [];

  bool dfs(int course) {
    if (cycle.contains(course)) return false;
    if (visited.contains(course)) return true;

    cycle.add(course);
    for (int pre in preReq[course]) {
      if (!dfs(pre)) return false;
    }
    cycle.remove(course);

    visited.add(course);
    result.add(course);
    return true;
  }

  for (int i = 0; i < numCourses; i++) {
    if (!dfs(i)) return [];
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public int[] FindOrder(int numCourses, int[][] prerequisites) {
        List<int>[] preReq = new List<int>[numCourses];
        for (int i = 0; i < numCourses; i++) preReq[i] = new List<int>();
        foreach (var pair in prerequisites) preReq[pair[0]].Add(pair[1]);

        HashSet<int> visited = new HashSet<int>();
        HashSet<int> cycle = new HashSet<int>();
        List<int> result = new List<int>();

        bool Dfs(int course) {
            if (cycle.Contains(course)) return false;
            if (visited.Contains(course)) return true;

            cycle.Add(course);
            foreach (var pre in preReq[course]) {
                if (!Dfs(pre)) return false;
            }
            cycle.Remove(course);

            visited.Add(course);
            result.Add(course);
            return true;
        }

        for (int i = 0; i < numCourses; i++) {
            if (!Dfs(i)) return new int[0];
        }

        return result.ToArray();
    }
}
```

### Java

```java
class Solution {
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        List<Integer>[] preReq = new ArrayList[numCourses];
        for (int i = 0; i < numCourses; i++) preReq[i] = new ArrayList<>();
        for (int[] pair : prerequisites) preReq[pair[0]].add(pair[1]);

        Set<Integer> visited = new HashSet<>();
        Set<Integer> cycle = new HashSet<>();
        List<Integer> result = new ArrayList<>();

        boolean dfs(int course) {
            if (cycle.contains(course)) return false;
            if (visited.contains(course)) return true;

            cycle.add(course);
            for (int pre : preReq[course]) {
                if (!dfs(pre)) return false;
            }
            cycle.remove(course);

            visited.add(course);
            result.add(course);
            return true;
        }

        for (int i = 0; i < numCourses; i++) {
            if (!dfs(i)) return new int[0];
        }

        return result.stream().mapToInt(i -> i).toArray();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun findOrder(numCourses: Int, prerequisites: Array<IntArray>): IntArray {
        val preReq = MutableList(numCourses) { mutableListOf<Int>() }
        prerequisites.forEach { (course, preq) -> preReq[course].add(preq) }

        val visited = mutableSetOf<Int>()
        val cycle = mutableSetOf<Int>()
        val ans = mutableListOf<Int>()

        fun dfs(course: Int): Boolean {
            if (course in cycle) return false
            if (course in visited) return true

            cycle += course
            preReq[course].forEach { if (!dfs(it)) return false }
            cycle -= course

            visited += course
            ans += course
            return true
        }

        repeat(numCourses) { if (!dfs(it)) return intArrayOf() }

        return ans.toIntArray()
    }
}
```

### Swift

```swift
class Solution {
    func findOrder(_ numCourses: Int, _ prerequisites: [[Int]]) -> [Int] {
        var preReq = Array(repeating: [Int](), count: numCourses)
        for pair in prerequisites {
            preReq[pair[0]].append(pair[1])
        }

        var visited = Set<Int>()
        var cycle = Set<Int>()
        var result = [Int]()

        func dfs(_ course: Int) -> Bool {
            if cycle.contains(course) { return false }
            if visited.contains(course) { return true }

            cycle.insert(course)
            for pre in preReq[course] {
                if !dfs(pre) { return false }
            }
            cycle.remove(course)

            visited.insert(course)
            result.append(course)
            return true
        }

        for i in 0..<numCourses {
            if !dfs(i) { return [] }
        }

        return result
    }
}
```



### The End

