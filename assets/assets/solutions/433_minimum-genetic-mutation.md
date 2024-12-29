# Minimum Genetic Mutation

## Problem Statement

A gene string can be represented by an 8-character long string, where each character is one of `'A'`, `'C'`, `'G'`, or `'T'`. A mutation is defined as a single character change in the gene string.

Given two gene strings `start` and `end`, and a list of valid gene mutations `bank`, return the minimum number of mutations needed to transform `start` into `end`. If no such mutation sequence exists, return `-1`.

A gene string can only mutate into another gene string if it is in the `bank`.

## Input

```text
start = "AACCGGTT"
end = "AACCGGTA"
bank = ["AACCGGTA"]
```

## Output

```text
1
```

## Solutions

### Dart

```dart
import 'dart:collection';

int minMutation(String start, String end, List<String> bank) {
  final bankSet = bank.toSet();
  if (!bankSet.contains(end)) return -1;

  final visited = <String>{};
  final queue = Queue<MapEntry<String, int>>();
  const mutations = ['A', 'C', 'G', 'T'];

  queue.add(MapEntry(start, 0));
  visited.add(start);

  while (queue.isNotEmpty) {
    final current = queue.removeFirst();
    final gene = current.key;
    final steps = current.value;

    if (gene == end) return steps;

    final chars = gene.split('');
    for (int i = 0; i < chars.length; i++) {
      final original = chars[i];
      for (final mutation in mutations) {
        if (mutation == original) continue;
        chars[i] = mutation;
        final mutated = chars.join('');
        if (bankSet.contains(mutated) && !visited.contains(mutated)) {
          queue.add(MapEntry(mutated, steps + 1));
          visited.add(mutated);
        }
      }
      chars[i] = original;
    }
  }
  return -1;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public int MinMutation(string start, string end, string[] bank) {
        var bankSet = new HashSet<string>(bank);
        if (!bankSet.Contains(end)) return -1;

        var visited = new HashSet<string>();
        var queue = new Queue<KeyValuePair<string, int>>();
        var mutations = new[] { 'A', 'C', 'G', 'T' };

        queue.Enqueue(new KeyValuePair<string, int>(start, 0));
        visited.Add(start);

        while (queue.Count > 0) {
            var current = queue.Dequeue();
            var gene = current.Key;
            var steps = current.Value;

            if (gene == end) return steps;

            var chars = gene.ToCharArray();
            for (int i = 0; i < chars.Length; i++) {
                char original = chars[i];
                foreach (var mutation in mutations) {
                    if (mutation == original) continue;
                    chars[i] = mutation;
                    string mutated = new string(chars);
                    if (bankSet.Contains(mutated) && !visited.Contains(mutated)) {
                        queue.Enqueue(new KeyValuePair<string, int>(mutated, steps + 1));
                        visited.Add(mutated);
                    }
                }
                chars[i] = original;
            }
        }
        return -1;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int minMutation(String start, String end, String[] bank) {
        Set<String> bankSet = new HashSet<>(Arrays.asList(bank));
        if (!bankSet.contains(end)) return -1;

        Set<String> visited = new HashSet<>();
        Queue<Pair<String, Integer>> queue = new LinkedList<>();
        char[] mutations = {'A', 'C', 'G', 'T'};

        queue.offer(new Pair<>(start, 0));
        visited.add(start);

        while (!queue.isEmpty()) {
            Pair<String, Integer> current = queue.poll();
            String gene = current.getKey();
            int steps = current.getValue();

            if (gene.equals(end)) return steps;

            char[] chars = gene.toCharArray();
            for (int i = 0; i < chars.length; i++) {
                char original = chars[i];
                for (char mutation : mutations) {
                    if (mutation == original) continue;
                    chars[i] = mutation;
                    String mutated = new String(chars);
                    if (bankSet.contains(mutated) && !visited.contains(mutated)) {
                        queue.offer(new Pair<>(mutated, steps + 1));
                        visited.add(mutated);
                    }
                }
                chars[i] = original;
            }
        }
        return -1;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun minMutation(start: String, end: String, bank: Array<String>): Int {
        val bankSet = bank.toHashSet()
        if (!bankSet.contains(end)) return -1
        val visited = mutableSetOf<String>()
        val queue = LinkedList<Pair<String, Int>>()
        val mutations = setOf('A', 'C', 'G', 'T')

        queue.offer(Pair(start, 0))
        visited.add(start)

        while (queue.isNotEmpty()) {
            val (current, steps) = queue.poll()
            if (current == end) return steps
            val chars = current.toCharArray()

            for (i in chars.indices) {
                val original = chars[i]
                for (mutation in mutations) {
                    if (mutation == original) continue
                    chars[i] = mutation
                    val mutated = String(chars)
                    if (mutated in bankSet && mutated !in visited) {
                        queue.offer(Pair(mutated, steps + 1))
                        visited.add(mutated)
                    }
                }
                chars[i] = original
            }
        }
        return -1
    }
}
```

### Swift

```swift
class Solution {
    func minMutation(_ start: String, _ end: String, _ bank: [String]) -> Int {
        let bankSet = Set(bank)
        if !bankSet.contains(end) { return -1 }

        var visited = Set<String>()
        var queue = [(start, 0)]
        let mutations: [Character] = ["A", "C", "G", "T"]

        while !queue.isEmpty {
            let (current, steps) = queue.removeFirst()
            if current == end { return steps }

            var chars = Array(current)
            for i in 0..<chars.count {
                let original = chars[i]
                for mutation in mutations {
                    if mutation == original { continue }
                    chars[i] = mutation
                    let mutated = String(chars)
                    if bankSet.contains(mutated) && !visited.contains(mutated) {
                        queue.append((mutated, steps + 1))
                        visited.insert(mutated)
                    }
                }
                chars[i] = original
            }
        }
        return -1
    }
}
```

### The End