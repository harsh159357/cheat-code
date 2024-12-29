# Smallest Number in Infinite Set

## Problem Statement

You have an infinite set of positive integers starting from `1`. You need to implement a data structure that supports the following operations:

1. `popSmallest`: Removes and returns the smallest integer in the set.
2. `addBack`: Adds a positive integer back into the set if it is not already present.

## Input Example

```text
Operations: ["SmallestInfiniteSet", "popSmallest", "popSmallest", "addBack", "popSmallest"]
Arguments: [[], [], [], [2], []]
```

## Output Example

```text
[null, 1, 2, null, 2]
```

## Solutions

### Kotlin

```kotlin
class SmallestInfiniteSet() {

    private var maxEverPopped = 0
    private val sortedAddedBack = sortedSetOf<Int>()

    // Pop the smallest number
    fun popSmallest(): Int {
        return if (sortedAddedBack.isEmpty()) {
            maxEverPopped++
            maxEverPopped
        } else {
            sortedAddedBack.pollFirst()
        }
    }

    // Add a number back to the set
    fun addBack(num: Int) {
        val isPopped = num <= maxEverPopped && num !in sortedAddedBack
        if (isPopped) {
            sortedAddedBack.add(num)
        }
    }
}

fun main() {
    val smallestSet = SmallestInfiniteSet()
    println(smallestSet.popSmallest()) // Output: 1
    println(smallestSet.popSmallest()) // Output: 2
    smallestSet.addBack(2)
    println(smallestSet.popSmallest()) // Output: 2
}
```

---

### Dart

```dart
import 'dart:collection';

class SmallestInfiniteSet {
  int maxEverPopped = 0;
  SplayTreeSet<int> sortedAddedBack = SplayTreeSet();

  int popSmallest() {
    if (sortedAddedBack.isEmpty) {
      maxEverPopped++;
      return maxEverPopped;
    } else {
      return sortedAddedBack.first..sortedAddedBack.remove(sortedAddedBack.first);
    }
  }

  void addBack(int num) {
    if (num <= maxEverPopped && !sortedAddedBack.contains(num)) {
      sortedAddedBack.add(num);
    }
  }
}

void main() {
  var smallestSet = SmallestInfiniteSet();
  print(smallestSet.popSmallest()); // Output: 1
  print(smallestSet.popSmallest()); // Output: 2
  smallestSet.addBack(2);
  print(smallestSet.popSmallest()); // Output: 2
}
```

---

### C#

```csharp
using System;
using System.Collections.Generic;

public class SmallestInfiniteSet {
    private int maxEverPopped = 0;
    private SortedSet<int> sortedAddedBack = new();

    public int PopSmallest() {
        if (sortedAddedBack.Count == 0) {
            maxEverPopped++;
            return maxEverPopped;
        } else {
            int smallest = sortedAddedBack.Min;
            sortedAddedBack.Remove(smallest);
            return smallest;
        }
    }

    public void AddBack(int num) {
        if (num <= maxEverPopped && !sortedAddedBack.Contains(num)) {
            sortedAddedBack.Add(num);
        }
    }
}

class Program {
    static void Main(string[] args) {
        SmallestInfiniteSet smallestSet = new();
        Console.WriteLine(smallestSet.PopSmallest()); // Output: 1
        Console.WriteLine(smallestSet.PopSmallest()); // Output: 2
        smallestSet.AddBack(2);
        Console.WriteLine(smallestSet.PopSmallest()); // Output: 2
    }
}
```

---

### Swift

```swift
import Foundation

class SmallestInfiniteSet {
    private var maxEverPopped = 0
    private var sortedAddedBack = SortedSet<Int>()

    func popSmallest() -> Int {
        if sortedAddedBack.isEmpty {
            maxEverPopped += 1
            return maxEverPopped
        } else {
            return sortedAddedBack.removeFirst()
        }
    }

    func addBack(_ num: Int) {
        if num <= maxEverPopped && !sortedAddedBack.contains(num) {
            sortedAddedBack.insert(num)
        }
    }
}

let smallestSet = SmallestInfiniteSet()
print(smallestSet.popSmallest()) // Output: 1
print(smallestSet.popSmallest()) // Output: 2
smallestSet.addBack(2)
print(smallestSet.popSmallest()) // Output: 2
```

### The End