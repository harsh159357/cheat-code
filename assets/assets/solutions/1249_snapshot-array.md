# Snapshot Array

## Problem Statement

Implement a data structure `SnapshotArray` that supports the following operations:

1. **`SnapshotArray(length: Int)`**: Initializes the array with the given length, with each element initialized to `0`.
2. **`set(index: Int, val: Int)`**: Sets the value at the given index in the array to `val`.
3. **`snap(): Int`**: Takes a snapshot of the array and returns the snapshot ID.
4. **`get(index: Int, snap_id: Int): Int`**: Returns the value at the given index in the snapshot with the given `snap_id`.

## Input Example

```text
["SnapshotArray", "set", "snap", "set", "get"]
[[3], [0, 5], [], [0, 6], [0, 0]]
```

## Output Example

```text
[null, null, 0, null, 5]
```

## Solutions

### Kotlin

```kotlin
class SnapshotArray(length: Int) {
    private val snapshots = mutableListOf<MutableMap<Int, Int>>()
    private var snapId = 0

    init {
        snapshots.add(mutableMapOf())
    }

    fun set(index: Int, `val`: Int) {
        snapshots[snapId][index] = `val`
    }

    fun snap(): Int {
        snapshots.add(mutableMapOf())
        return snapId++
    }

    fun get(index: Int, snap_id: Int): Int {
        var id = snap_id
        while (id >= 0) {
            if (snapshots[id].containsKey(index)) {
                return snapshots[id][index]!!
            }
            id--
        }
        return 0
    }
}
```

### Dart

```dart
class SnapshotArray {
  List<Map<int, int>> snapshots = [{}];
  int snapId = 0;

  SnapshotArray(int length);

  void set(int index, int val) {
    snapshots[snapId][index] = val;
  }

  int snap() {
    snapshots.add({});
    return snapId++;
  }

  int get(int index, int snap_id) {
    int id = snap_id;
    while (id >= 0) {
      if (snapshots[id].containsKey(index)) {
        return snapshots[id][index]!;
      }
      id--;
    }
    return 0;
  }
}
```

### C#

```csharp
using System.Collections.Generic;

public class SnapshotArray {
    private List<Dictionary<int, int>> snapshots = new List<Dictionary<int, int>>();
    private int snapId = 0;

    public SnapshotArray(int length) {
        snapshots.Add(new Dictionary<int, int>());
    }

    public void Set(int index, int val) {
        snapshots[snapId][index] = val;
    }

    public int Snap() {
        snapshots.Add(new Dictionary<int, int>());
        return snapId++;
    }

    public int Get(int index, int snap_id) {
        int id = snap_id;
        while (id >= 0) {
            if (snapshots[id].ContainsKey(index)) {
                return snapshots[id][index];
            }
            id--;
        }
        return 0;
    }
}
```

### Java

```java
import java.util.*;

class SnapshotArray {
    private List<Map<Integer, Integer>> snapshots = new ArrayList<>();
    private int snapId = 0;

    public SnapshotArray(int length) {
        snapshots.add(new HashMap<>());
    }

    public void set(int index, int val) {
        snapshots.get(snapId).put(index, val);
    }

    public int snap() {
        snapshots.add(new HashMap<>());
        return snapId++;
    }

    public int get(int index, int snap_id) {
        int id = snap_id;
        while (id >= 0) {
            if (snapshots.get(id).containsKey(index)) {
                return snapshots.get(id).get(index);
            }
            id--;
        }
        return 0;
    }
}
```

### Swift

```swift
class SnapshotArray {
    private var snapshots: [Dictionary<Int, Int>]
    private var snapId: Int

    init(_ length: Int) {
        snapshots = [[:]]
        snapId = 0
    }

    func set(_ index: Int, _ val: Int) {
        snapshots[snapId][index] = val
    }

    func snap() -> Int {
        snapshots.append([:])
        let currentSnapId = snapId
        snapId += 1
        return currentSnapId
    }

    func get(_ index: Int, _ snap_id: Int) -> Int {
        var id = snap_id
        while id >= 0 {
            if let value = snapshots[id][index] {
                return value
            }
            id -= 1
        }
        return 0
    }
}
```

### The End