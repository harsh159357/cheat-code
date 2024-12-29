# LRU Cache

## Problem Statement

Design a data structure that follows the constraints of a **Least Recently Used (LRU) Cache**. Implement the `LRUCache` class:

- `LRUCache(int capacity)` Initializes the LRU cache with a positive size `capacity`.
- `int get(int key)` Returns the value of the `key` if the key exists in the cache. Otherwise, returns `-1`.
- `void put(int key, int value)` Updates the value of the `key` if the key exists. Otherwise, adds the `key-value` pair to the cache. If the number of keys exceeds the capacity from this operation, evicts the least recently used key.

The functions `get` and `put` must run in **O(1)** average time complexity.

---

## Solutions

### Dart

```dart
class LRUCache {
  final int capacity;
  final LinkedHashMap<int, int> cache;

  LRUCache(this.capacity) : cache = LinkedHashMap<int, int>();

  int get(int key) {
    if (!cache.containsKey(key)) return -1;
    int value = cache.remove(key)!;
    cache[key] = value; // Re-insert to update usage
    return value;
  }

  void put(int key, int value) {
    if (cache.containsKey(key)) {
      cache.remove(key);
    } else if (cache.length == capacity) {
      cache.remove(cache.keys.first); // Remove least recently used
    }
    cache[key] = value;
  }
}
```


### C#

```csharp
using System.Collections.Generic;

public class LRUCache {
    private int Capacity;
    private LinkedHashMap<int, int> Cache;

    public LRUCache(int capacity) {
        Capacity = capacity;
        Cache = new LinkedHashMap<int, int>();
    }

    public int Get(int key) {
        if (!Cache.ContainsKey(key)) return -1;
        int value = Cache[key];
        Cache.Remove(key);
        Cache[key] = value;
        return value;
    }

    public void Put(int key, int value) {
        if (Cache.ContainsKey(key)) {
            Cache.Remove(key);
        } else if (Cache.Count == Capacity) {
            Cache.Remove(Cache.Keys.First());
        }
        Cache[key] = value;
    }
}
```


### Java

```java
import java.util.LinkedHashMap;

class LRUCache {
    private int capacity;
    private LinkedHashMap<Integer, Integer> cache;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        this.cache = new LinkedHashMap<>(capacity, 0.75f, true);
    }

    public int get(int key) {
        return cache.getOrDefault(key, -1);
    }

    public void put(int key, int value) {
        cache.put(key, value);
        if (cache.size() > capacity) {
            cache.remove(cache.keySet().iterator().next());
        }
    }
}
```


### Kotlin

```kotlin
class LRUCache(private val capacity: Int) {
    private val map = LinkedHashMap<Int, Int>(capacity, 0.75f, true)

    fun get(key: Int): Int {
        return map.getOrDefault(key, -1)
    }

    fun put(key: Int, value: Int) {
        map[key] = value
        if (map.size > capacity) {
            val iterator = map.iterator()
            iterator.next()
            iterator.remove()
        }
    }
}
```


### Swift

```swift
class LRUCache {
    private let capacity: Int
    private var cache: [Int: Int]
    private var usageOrder: [Int]

    init(_ capacity: Int) {
        self.capacity = capacity
        self.cache = [:]
        self.usageOrder = []
    }

    func get(_ key: Int) -> Int {
        guard let value = cache[key] else { return -1 }
        if let index = usageOrder.firstIndex(of: key) {
            usageOrder.remove(at: index)
        }
        usageOrder.append(key)
        return value
    }

    func put(_ key: Int, _ value: Int) {
        if let index = usageOrder.firstIndex(of: key) {
            usageOrder.remove(at: index)
        } else if usageOrder.count == capacity {
            let leastUsed = usageOrder.removeFirst()
            cache.removeValue(forKey: leastUsed)
        }
        usageOrder.append(key)
        cache[key] = value
    }
}
```


### The End

