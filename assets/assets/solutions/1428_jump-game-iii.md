# Jump Game III

## Problem Statement

Given an array of non-negative integers `arr` and an integer `start`, determine if you can reach any index with value `0` by starting at index `start` and repeatedly jumping either left or right by the value at the current index.

Return `true` if you can reach any such index, or `false` otherwise.

## Input

```text
arr = [4, 2, 3, 0, 3, 1, 2]
start = 5
```

## Output

```text
true
```


## Solutions

### Kotlin

```kotlin
import java.util.LinkedList

class Solution {
    fun canReach(arr: IntArray, start: Int): Boolean {
        val queue = LinkedList<Int>()
        val visited = BooleanArray(arr.size)
        queue.offer(start)
        visited[start] = true

        while (queue.isNotEmpty()) {
            val currentIndex = queue.poll()
            if (arr[currentIndex] == 0) return true

            val leftIndex = currentIndex - arr[currentIndex]
            val rightIndex = currentIndex + arr[currentIndex]

            if (leftIndex >= 0 && !visited[leftIndex]) {
                queue.offer(leftIndex)
                visited[leftIndex] = true
            }

            if (rightIndex < arr.size && !visited[rightIndex]) {
                queue.offer(rightIndex)
                visited[rightIndex] = true
            }
        }

        return false
    }
}
```

### Dart

```dart
bool canReach(List<int> arr, int start) {
  Queue<int> queue = Queue();
  List<bool> visited = List.filled(arr.length, false);
  queue.add(start);
  visited[start] = true;

  while (queue.isNotEmpty) {
    int currentIndex = queue.removeFirst();
    if (arr[currentIndex] == 0) return true;

    int leftIndex = currentIndex - arr[currentIndex];
    int rightIndex = currentIndex + arr[currentIndex];

    if (leftIndex >= 0 && !visited[leftIndex]) {
      queue.add(leftIndex);
      visited[leftIndex] = true;
    }

    if (rightIndex < arr.length && !visited[rightIndex]) {
      queue.add(rightIndex);
      visited[rightIndex] = true;
    }
  }

  return false;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public bool CanReach(int[] arr, int start) {
        Queue<int> queue = new Queue<int>();
        bool[] visited = new bool[arr.Length];
        queue.Enqueue(start);
        visited[start] = true;

        while (queue.Count > 0) {
            int currentIndex = queue.Dequeue();
            if (arr[currentIndex] == 0) return true;

            int leftIndex = currentIndex - arr[currentIndex];
            int rightIndex = currentIndex + arr[currentIndex];

            if (leftIndex >= 0 && !visited[leftIndex]) {
                queue.Enqueue(leftIndex);
                visited[leftIndex] = true;
            }

            if (rightIndex < arr.Length && !visited[rightIndex]) {
                queue.Enqueue(rightIndex);
                visited[rightIndex] = true;
            }
        }

        return false;
    }
}
```

### Java

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public boolean canReach(int[] arr, int start) {
        Queue<Integer> queue = new LinkedList<>();
        boolean[] visited = new boolean[arr.length];
        queue.offer(start);
        visited[start] = true;

        while (!queue.isEmpty()) {
            int currentIndex = queue.poll();
            if (arr[currentIndex] == 0) return true;

            int leftIndex = currentIndex - arr[currentIndex];
            int rightIndex = currentIndex + arr[currentIndex];

            if (leftIndex >= 0 && !visited[leftIndex]) {
                queue.offer(leftIndex);
                visited[leftIndex] = true;
            }

            if (rightIndex < arr.length && !visited[rightIndex]) {
                queue.offer(rightIndex);
                visited[rightIndex] = true;
            }
        }

        return false;
    }
}
```

### Swift

```swift
class Solution {
    func canReach(_ arr: [Int], _ start: Int) -> Bool {
        var queue = [start]
        var visited = Array(repeating: false, count: arr.count)
        visited[start] = true

        while !queue.isEmpty {
            let currentIndex = queue.removeFirst()
            if arr[currentIndex] == 0 {
                return true
            }

            let leftIndex = currentIndex - arr[currentIndex]
            let rightIndex = currentIndex + arr[currentIndex]

            if leftIndex >= 0 && !visited[leftIndex] {
                queue.append(leftIndex)
                visited[leftIndex] = true
            }

            if rightIndex < arr.count && !visited[rightIndex] {
                queue.append(rightIndex)
                visited[rightIndex] = true
            }
        }

        return false
    }
}
```

### The End