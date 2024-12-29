# Course Schedule

## Problem Statement

You are given `numCourses` courses labeled from `0` to `numCourses - 1` and an array `prerequisites` where `prerequisites[i] = [a, b]` indicates that you must take course `b` before course `a`.

Return `true` if you can finish all courses, otherwise return `false`.

## Input

```text
numCourses = 2, prerequisites = [[1, 0]]
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool canFinish(int numCourses, List<List<int>> prerequisites) {
  List<List<int>> adjList = List.generate(numCourses, (_) => []);
  List<int> indegree = List.filled(numCourses, 0);

  for (var prerequisite in prerequisites) {
    adjList[prerequisite[1]].add(prerequisite[0]);
    indegree[prerequisite[0]]++;
  }

  Queue<int> queue = Queue();
  for (int i = 0; i < numCourses; i++) {
    if (indegree[i] == 0) queue.add(i);
  }

  int completedCourses = 0;
  while (queue.isNotEmpty) {
    int course = queue.removeFirst();
    completedCourses++;
    for (int neighbor in adjList[course]) {
      indegree[neighbor]--;
      if (indegree[neighbor] == 0) queue.add(neighbor);
    }
  }

  return completedCourses == numCourses;
}
```

### C#

```csharp
public class Solution {
    public bool CanFinish(int numCourses, int[][] prerequisites) {
        List<int>[] adjList = new List<int>[numCourses];
        int[] indegree = new int[numCourses];
        for (int i = 0; i < numCourses; i++) adjList[i] = new List<int>();

        foreach (var prerequisite in prerequisites) {
            adjList[prerequisite[1]].Add(prerequisite[0]);
            indegree[prerequisite[0]]++;
        }

        Queue<int> queue = new Queue<int>();
        for (int i = 0; i < numCourses; i++) {
            if (indegree[i] == 0) queue.Enqueue(i);
        }

        int completedCourses = 0;
        while (queue.Count > 0) {
            int course = queue.Dequeue();
            completedCourses++;
            foreach (int neighbor in adjList[course]) {
                indegree[neighbor]--;
                if (indegree[neighbor] == 0) queue.Enqueue(neighbor);
            }
        }

        return completedCourses == numCourses;
    }
}
```

### Java

```java
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<List<Integer>> adjList = new ArrayList<>();
        int[] indegree = new int[numCourses];

        for (int i = 0; i < numCourses; i++) {
            adjList.add(new ArrayList<>());
        }

        for (int[] prerequisite : prerequisites) {
            adjList.get(prerequisite[1]).add(prerequisite[0]);
            indegree[prerequisite[0]]++;
        }

        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < numCourses; i++) {
            if (indegree[i] == 0) queue.add(i);
        }

        int completedCourses = 0;
        while (!queue.isEmpty()) {
            int course = queue.poll();
            completedCourses++;
            for (int neighbor : adjList.get(course)) {
                indegree[neighbor]--;
                if (indegree[neighbor] == 0) queue.add(neighbor);
            }
        }

        return completedCourses == numCourses;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun canFinish(numCourses: Int, prerequisites: Array<IntArray>): Boolean {
        val adjList = Array(numCourses) { mutableListOf<Int>() }
        val indegree = IntArray(numCourses)

        for (prerequisite in prerequisites) {
            adjList[prerequisite[1]].add(prerequisite[0])
            indegree[prerequisite[0]]++
        }

        val queue = LinkedList<Int>()
        for (i in 0 until numCourses) {
            if (indegree[i] == 0) queue.offer(i)
        }

        var completedCourses = 0
        while (queue.isNotEmpty()) {
            val course = queue.poll()
            completedCourses++
            for (neighbor in adjList[course]) {
                indegree[neighbor]--
                if (indegree[neighbor] == 0) queue.offer(neighbor)
            }
        }

        return completedCourses == numCourses
    }
}
```

### Swift

```swift
class Solution {
    func canFinish(_ numCourses: Int, _ prerequisites: [[Int]]) -> Bool {
        var adjList = [[Int]](repeating: [], count: numCourses)
        var indegree = [Int](repeating: 0, count: numCourses)

        for prerequisite in prerequisites {
            adjList[prerequisite[1]].append(prerequisite[0])
            indegree[prerequisite[0]] += 1
        }

        var queue = [Int]()
        for i in 0..<numCourses {
            if indegree[i] == 0 {
                queue.append(i)
            }
        }

        var completedCourses = 0
        while !queue.isEmpty {
            let course = queue.removeFirst()
            completedCourses += 1
            for neighbor in adjList[course] {
                indegree[neighbor] -= 1
                if indegree[neighbor] == 0 {
                    queue.append(neighbor)
                }
            }
        }

        return completedCourses == numCourses
    }
}
```



### The End

