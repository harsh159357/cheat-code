# Insert Delete GetRandom O(1)

## Problem Statement

Implement the `RandomizedSet` class:

1. `bool insert(int val)` Inserts an item `val` into the set if not already present. Returns `true` if the item was not present, `false` otherwise.
2. `bool remove(int val)` Removes an item `val` from the set if present. Returns `true` if the item was present, `false` otherwise.
3. `int getRandom()` Returns a random element from the current set of elements. Each element must have the same probability of being returned.

The methods must run in **O(1)** average time complexity.

---

## Input

```text
Operations: ["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
Values: [[], [1], [2], [2], [], [1], [2], []]
```

## Output

```text
[null, true, false, true, 1, true, false, 2]
```


## Solutions

### Dart

```dart
import 'dart:math';

class RandomizedSet {
  final Map<int, int> _map = {};
  final List<int> _list = [];
  final Random _random = Random();

  bool insert(int val) {
    if (_map.containsKey(val)) return false;
    _map[val] = _list.length;
    _list.add(val);
    return true;
  }

  bool remove(int val) {
    if (!_map.containsKey(val)) return false;
    final int indexToRemove = _map[val]!;
    final int lastElement = _list.last;
    _list[indexToRemove] = lastElement;
    _map[lastElement] = indexToRemove;
    _list.removeLast();
    _map.remove(val);
    return true;
  }

  int getRandom() {
    return _list[_random.nextInt(_list.length)];
  }
}
```


### C#

```csharp
using System;
using System.Collections.Generic;

public class RandomizedSet {
    private Dictionary<int, int> map;
    private List<int> list;
    private Random random;

    public RandomizedSet() {
        map = new Dictionary<int, int>();
        list = new List<int>();
        random = new Random();
    }

    public bool Insert(int val) {
        if (map.ContainsKey(val)) return false;
        map[val] = list.Count;
        list.Add(val);
        return true;
    }

    public bool Remove(int val) {
        if (!map.ContainsKey(val)) return false;
        int indexToRemove = map[val];
        int lastElement = list[^1];
        list[indexToRemove] = lastElement;
        map[lastElement] = indexToRemove;
        list.RemoveAt(list.Count - 1);
        map.Remove(val);
        return true;
    }

    public int GetRandom() {
        return list[random.Next(list.Count)];
    }
}
```


### Java

```java
import java.util.*;

class RandomizedSet {
    private Map<Integer, Integer> map;
    private List<Integer> list;
    private Random random;

    public RandomizedSet() {
        map = new HashMap<>();
        list = new ArrayList<>();
        random = new Random();
    }

    public boolean insert(int val) {
        if (map.containsKey(val)) return false;
        map.put(val, list.size());
        list.add(val);
        return true;
    }

    public boolean remove(int val) {
        if (!map.containsKey(val)) return false;
        int indexToRemove = map.get(val);
        int lastElement = list.get(list.size() - 1);
        list.set(indexToRemove, lastElement);
        map.put(lastElement, indexToRemove);
        list.remove(list.size() - 1);
        map.remove(val);
        return true;
    }

    public int getRandom() {
        return list.get(random.nextInt(list.size()));
    }
}
```

### Kotlin

```kotlin
import kotlin.random.Random

class RandomizedSet {
    private val map = mutableMapOf<Int, Int>()
    private val list = mutableListOf<Int>()

    fun insert(`val`: Int): Boolean {
        if (`val` in map) return false
        map[`val`] = list.size
        list.add(`val`)
        return true
    }

    fun remove(`val`: Int): Boolean {
        if (`val` !in map) return false
        val indexToRemove = map[`val`]!!
        val lastElement = list.last()
        list[indexToRemove] = lastElement
        map[lastElement] = indexToRemove
        list.removeAt(list.size - 1)
        map.remove(`val`)
        return true
    }

    fun getRandom(): Int {
        return list[Random.nextInt(list.size)]
    }
}
```

### Swift

```swift
import Foundation

class RandomizedSet {
    private var map = [Int: Int]()
    private var list = [Int]()

    func insert(_ val: Int) -> Bool {
        if map[val] != nil { return false }
        map[val] = list.count
        list.append(val)
        return true
    }

    func remove(_ val: Int) -> Bool {
        guard let indexToRemove = map[val] else { return false }
        let lastElement = list.last!
        list[indexToRemove] = lastElement
        map[lastElement] = indexToRemove
        list.removeLast()
        map.removeValue(forKey: val)
        return true
    }

    func getRandom() -> Int {
        return list.randomElement()!
    }
}
```


### The End