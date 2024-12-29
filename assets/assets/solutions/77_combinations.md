# Combinations

## Problem Statement

Given two integers `n` and `k`, return all possible combinations of `k` numbers out of the range `[1, n]`.

You may return the answer in **any order**.

## Input

```text
n = 4, k = 2
```

## Output

```text
[
  [1, 2],
  [1, 3],
  [1, 4],
  [2, 3],
  [2, 4],
  [3, 4]
]
```

## Solutions

### Dart

```dart
List<List<int>> combine(int n, int k) {
  List<List<int>> result = [];
  void backtrack(int start, List<int> combination) {
    if (combination.length == k) {
      result.add(List.from(combination));
      return;
    }
    for (int i = start; i <= n; i++) {
      combination.add(i);
      backtrack(i + 1, combination);
      combination.removeLast();
    }
  }
  backtrack(1, []);
  return result;
}

void main() {
  print(combine(4, 2)); // Output: [[1, 2], [1, 3], [1, 4], [2, 3], [2, 4], [3, 4]]
}
```

### C#

```csharp
public class Solution {
    public IList<IList<int>> Combine(int n, int k) {
        IList<IList<int>> result = new List<IList<int>>();
        void Backtrack(int start, IList<int> combination) {
            if (combination.Count == k) {
                result.Add(new List<int>(combination));
                return;
            }
            for (int i = start; i <= n; i++) {
                combination.Add(i);
                Backtrack(i + 1, combination);
                combination.RemoveAt(combination.Count - 1);
            }
        }
        Backtrack(1, new List<int>());
        return result;
    }
}
```

### Java

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(n, k, 1, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int n, int k, int start, List<Integer> combination, List<List<Integer>> result) {
        if (combination.size() == k) {
            result.add(new ArrayList<>(combination));
            return;
        }
        for (int i = start; i <= n; i++) {
            combination.add(i);
            backtrack(n, k, i + 1, combination, result);
            combination.remove(combination.size() - 1);
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun combine(n: Int, k: Int): List<List<Int>> {
        val result = mutableListOf<List<Int>>()
        backtrack(n, k, 1, mutableListOf(), result)
        return result
    }

    private fun backtrack(n: Int, k: Int, start: Int, combination: MutableList<Int>, result: MutableList<List<Int>>) {
        if (combination.size == k) {
            result.add(ArrayList(combination))
            return
        }
        for (i in start..n) {
            combination.add(i)
            backtrack(n, k, i + 1, combination, result)
            combination.removeAt(combination.size - 1)
        }
    }
}

fun main() {
    val solution = Solution()
    println(solution.combine(4, 2)) // Output: [[1, 2], [1, 3], [1, 4], [2, 3], [2, 4], [3, 4]]
}
```

### Swift

```swift
class Solution {
    func combine(_ n: Int, _ k: Int) -> [[Int]] {
        var result = [[Int]]()

        func backtrack(_ start: Int, _ combination: inout [Int]) {
            if combination.count == k {
                result.append(combination)
                return
            }

            for i in start...n {
                combination.append(i)
                backtrack(i + 1, &combination)
                combination.removeLast()
            }
        }

        var combination = [Int]()
        backtrack(1, &combination)
        return result
    }
}

let solution = Solution()
print(solution.combine(4, 2)) // Output: [[1, 2], [1, 3], [1, 4], [2, 3], [2, 4], [3, 4]]
```


### The End

