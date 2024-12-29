# Keys and Rooms

## Problem Statement

There are `n` rooms labeled from `0` to `n-1`. Each room contains a list of keys to other rooms. Initially, you are in room `0`, and you can move freely between rooms as long as you have the key to enter that room.

Return `true` if you can visit all the rooms, otherwise return `false`.

## Input

```text
rooms = [[1], [2], [3], []]
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool canVisitAllRooms(List<List<int>> rooms) {
  List<bool> visited = List.filled(rooms.length, false);

  void dfs(int room) {
    if (visited[room]) return;
    visited[room] = true;
    for (int key in rooms[room]) {
      dfs(key);
    }
  }

  dfs(0);
  return visited.every((room) => room);
}
```

### C#

```csharp
public class Solution {
    public bool CanVisitAllRooms(IList<IList<int>> rooms) {
        bool[] visited = new bool[rooms.Count];

        void Dfs(int room) {
            if (visited[room]) return;
            visited[room] = true;
            foreach (int key in rooms[room]) {
                Dfs(key);
            }
        }

        Dfs(0);
        return visited.All(v => v);
    }
}
```

### Java

```java
import java.util.List;

class Solution {
    public boolean canVisitAllRooms(List<List<Integer>> rooms) {
        boolean[] visited = new boolean[rooms.size()];

        dfs(0, rooms, visited);

        for (boolean v : visited) {
            if (!v) return false;
        }

        return true;
    }

    private void dfs(int room, List<List<Integer>> rooms, boolean[] visited) {
        if (visited[room]) return;
        visited[room] = true;
        for (int key : rooms.get(room)) {
            dfs(key, rooms, visited);
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun canVisitAllRooms(rooms: List<List<Int>>): Boolean {
        val visited = BooleanArray(rooms.size)
        dfs(rooms, 0, visited)
        return visited.all { it }
    }

    private fun dfs(rooms: List<List<Int>>, room: Int, visited: BooleanArray) {
        if (visited[room]) return
        visited[room] = true
        for (key in rooms[room]) {
            dfs(rooms, key, visited)
        }
    }
}
```

### Swift

```swift
class Solution {
    func canVisitAllRooms(_ rooms: [[Int]]) -> Bool {
        var visited = [Bool](repeating: false, count: rooms.count)

        func dfs(_ room: Int) {
            if visited[room] { return }
            visited[room] = true
            for key in rooms[room] {
                dfs(key)
            }
        }

        dfs(0)
        return visited.allSatisfy { $0 }
    }
}
```

### The End