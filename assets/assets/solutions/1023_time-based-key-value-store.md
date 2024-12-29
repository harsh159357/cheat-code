# Time-Based Key-Value Store

## Problem Statement

Design a time-based key-value data structure that can store multiple values for the same key at different timestamps and retrieve the key's value at a certain timestamp.

Implement the `TimeMap` class:

- `TimeMap()` Initializes the object.
- `void set(String key, String value, int timestamp)` Stores the key-value pair along with the timestamp.
- `String get(String key, int timestamp)` Returns a value such that `set` was called previously with the same key and the timestamp is the largest among all timestamps less than or equal to `timestamp`. If there are no such timestamps, it returns `""`.

## Input

```text
["TimeMap", "set", "get", "get", "set", "get", "get"]
[[], ["foo", "bar", 1], ["foo", 1], ["foo", 3], ["foo", "bar2", 4], ["foo", 4], ["foo", 5]]
```

## Output

```text
[null, null, "bar", "bar", null, "bar2", "bar2"]
```

## Solutions

### Kotlin

```kotlin
import java.util.TreeMap

class TimeMap {

    private val map = mutableMapOf<String, TreeMap<Int, String>>()

    fun set(key: String, value: String, timestamp: Int) {
        if (!map.containsKey(key)) {
            map[key] = TreeMap()
        }
        map[key]!![timestamp] = value
    }

    fun get(key: String, timestamp: Int): String {
        val treeMap = map[key] ?: return ""
        val entry = treeMap.floorEntry(timestamp)
        return entry?.value ?: ""
    }
}
```

### Dart

```dart
class TimeMap {
  final Map<String, TreeMap<int, String>> map = {};

  void set(String key, String value, int timestamp) {
    map.putIfAbsent(key, () => TreeMap<int, String>());
    map[key]![timestamp] = value;
  }

  String get(String key, int timestamp) {
    if (!map.containsKey(key)) return "";
    final floorEntry = map[key]!.lastWhere((time) => time <= timestamp, orElse: () => null);
    return floorEntry?.value ?? "";
  }
}
```

### C#

```csharp
using System.Collections.Generic;

public class TimeMap {
    private Dictionary<string, SortedDictionary<int, string>> map;

    public TimeMap() {
        map = new Dictionary<string, SortedDictionary<int, string>>();
    }

    public void Set(string key, string value, int timestamp) {
        if (!map.ContainsKey(key)) {
            map[key] = new SortedDictionary<int, string>();
        }
        map[key][timestamp] = value;
    }

    public string Get(string key, int timestamp) {
        if (!map.ContainsKey(key)) return "";
        var tree = map[key];
        foreach (var kvp in tree.Reverse()) {
            if (kvp.Key <= timestamp) {
                return kvp.Value;
            }
        }
        return "";
    }
}
```

### Java

```java
import java.util.*;

class TimeMap {
    private Map<String, TreeMap<Integer, String>> map;

    public TimeMap() {
        map = new HashMap<>();
    }

    public void set(String key, String value, int timestamp) {
        map.computeIfAbsent(key, k -> new TreeMap<>()).put(timestamp, value);
    }

    public String get(String key, int timestamp) {
        if (!map.containsKey(key)) return "";
        Map.Entry<Integer, String> entry = map.get(key).floorEntry(timestamp);
        return entry != null ? entry.getValue() : "";
    }
}
```

### Swift

```swift
class TimeMap {
    private var map = [String: [Int: String]]()

    func set(_ key: String, _ value: String, _ timestamp: Int) {
        if map[key] == nil {
            map[key] = [:]
        }
        map[key]![timestamp] = value
    }

    func get(_ key: String, _ timestamp: Int) -> String {
        guard let tree = map[key] else { return "" }
        let keys = tree.keys.sorted()
        for time in keys.reversed() {
            if time <= timestamp {
                return tree[time]!
            }
        }
        return ""
    }
}
```

### The End