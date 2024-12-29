# Combination Sum III

## Problem Statement

Find all valid combinations of `k` numbers that sum up to `n` such that the following conditions are met:

1. Only numbers from `1` to `9` can be used.
2. Each combination should be a unique set of numbers.
3. Numbers in the combination should be distinct.

Return the list of all possible combinations.

## Input

```text
k = 3, n = 7
```

## Output

```text
[[1, 2, 4]]
```

## Solutions

### Dart

```dart
List<List<int>> combinationSum3(int k, int n) {
  List<List<int>> combinations = [];
  
  void backtrack(List<int> combination, int remain, int start) {
    if (combination.length == k && remain == 0) {
      combinations.add(List.of(combination));
      return;
    }
    if (combination.length == k || remain <= 0) return;

    for (int i = start; i <= 9; i++) {
      combination.add(i);
      backtrack(combination, remain - i, i + 1);
      combination.removeLast();
    }
  }

  backtrack([], n, 1);
  return combinations;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public IList<IList<int>> CombinationSum3(int k, int n) {
        var combinations = new List<IList<int>>();
        
        void Backtrack(List<int> combination, int remain, int start) {
            if (combination.Count == k && remain == 0) {
                combinations.Add(new List<int>(combination));
                return;
            }
            if (combination.Count == k || remain <= 0) return;

            for (int i = start; i <= 9; i++) {
                combination.Add(i);
                Backtrack(combination, remain - i, i + 1);
                combination.RemoveAt(combination.Count - 1);
            }
        }

        Backtrack(new List<int>(), n, 1);
        return combinations;
    }
}
```

### Java

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        List<List<Integer>> combinations = new ArrayList<>();
        backtrack(combinations, new ArrayList<>(), k, n, 1);
        return combinations;
    }

    private void backtrack(List<List<Integer>> combinations, List<Integer> combination, int k, int remain, int start) {
        if (combination.size() == k && remain == 0) {
            combinations.add(new ArrayList<>(combination));
            return;
        }
        if (combination.size() == k || remain <= 0) return;

        for (int i = start; i <= 9; i++) {
            combination.add(i);
            backtrack(combinations, combination, k - 1, remain - i, i + 1);
            combination.remove(combination.size() - 1);
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun combinationSum3(k: Int, n: Int): List<List<Int>> {
        val combinations = mutableListOf<List<Int>>()
        backtrack(combinations, mutableListOf(), k, n, 1)
        return combinations
    }

    private fun backtrack(
        combinations: MutableList<List<Int>>,
        combination: MutableList<Int>,
        k: Int,
        remain: Int,
        start: Int
    ) {
        if (k == 0 && remain == 0) {
            combinations.add(ArrayList(combination))
            return
        }
        if (k == 0 || remain <= 0) return
        for (i in start..9) {
            combination.add(i)
            backtrack(combinations, combination, k - 1, remain - i, i + 1)
            combination.removeAt(combination.size - 1)
        }
    }
}
```

### Swift

```swift
class Solution {
    func combinationSum3(_ k: Int, _ n: Int) -> [[Int]] {
        var combinations = [[Int]]()

        func backtrack(_ combination: inout [Int], _ remain: Int, _ start: Int) {
            if combination.count == k && remain == 0 {
                combinations.append(combination)
                return
            }
            if combination.count == k || remain <= 0 { return }

            for i in start...9 {
                combination.append(i)
                backtrack(&combination, remain - i, i + 1)
                combination.removeLast()
            }
        }

        var combination = [Int]()
        backtrack(&combination, n, 1)
        return combinations
    }
}
```

### The End

