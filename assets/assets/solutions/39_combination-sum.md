# Combination Sum

## Problem Statement

Given an array of distinct integers `candidates` and a target integer `target`, return a list of all unique combinations of `candidates` where the chosen numbers sum to `target`. You may return the combinations in any order.

The same number may be chosen from `candidates` an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

## Input

```text
candidates = [2,3,6,7], target = 7
```

## Output

```text
[[2,2,3],[7]]

(Explanation: These are the unique combinations that add up to the target value.)
```

## Solutions

### Dart

```dart
List<List<int>> combinationSum(List<int> candidates, int target) {
  List<List<int>> result = [];
  void backtrack(int remaining, int start, List<int> combination) {
    if (remaining < 0) return;
    if (remaining == 0) {
      result.add(List.from(combination));
      return;
    }

    for (int i = start; i < candidates.length; i++) {
      combination.add(candidates[i]);
      backtrack(remaining - candidates[i], i, combination);
      combination.removeLast();
    }
  }

  backtrack(target, 0, []);
  return result;
}

void main() {
  print(combinationSum([2, 3, 6, 7], 7)); // Output: [[2, 2, 3], [7]]
  print(combinationSum([2, 3, 5], 8)); // Output: [[2, 2, 2, 2], [2, 3, 3], [3, 5]]
}
```

### C#

```csharp
public class Solution {
    public IList<IList<int>> CombinationSum(int[] candidates, int target) {
        IList<IList<int>> result = new List<IList<int>>();
        void Backtrack(int remaining, int start, List<int> combination) {
            if (remaining < 0) return;
            if (remaining == 0) {
                result.Add(new List<int>(combination));
                return;
            }

            for (int i = start; i < candidates.Length; i++) {
                combination.Add(candidates[i]);
                Backtrack(remaining - candidates[i], i, combination);
                combination.RemoveAt(combination.Count - 1);
            }
        }

        Backtrack(target, 0, new List<int>());
        return result;
    }
}
```

### Java

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();

        backtrack(candidates, target, 0, new ArrayList<>(), result);

        return result;
    }

    private void backtrack(int[] candidates, int target, int start, List<Integer> combination, List<List<Integer>> result) {
        if (target < 0) return;
        if (target == 0) {
            result.add(new ArrayList<>(combination));
            return;
        }

        for (int i = start; i < candidates.length; i++) {
            combination.add(candidates[i]);
            backtrack(candidates, target - candidates[i], i, combination, result);
            combination.remove(combination.size() - 1);
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun combinationSum(candidates: IntArray, target: Int): List<List<Int>> {
        val result = mutableListOf<List<Int>>()

        fun backtrack(remaining: Int, start: Int, combination: MutableList<Int>) {
            if (remaining < 0) return
            if (remaining == 0) {
                result.add(ArrayList(combination))
                return
            }

            for (i in start until candidates.size) {
                combination.add(candidates[i])
                backtrack(remaining - candidates[i], i, combination)
                combination.removeAt(combination.size - 1)
            }
        }

        backtrack(target, 0, mutableListOf())
        return result
    }
}
```

### Swift

```swift
class Solution {
    func combinationSum(_ candidates: [Int], _ target: Int) -> [[Int]] {
        var result = [[Int]]()

        func backtrack(_ remaining: Int, _ start: Int, _ combination: inout [Int]) {
            if remaining < 0 { return }
            if remaining == 0 {
                result.append(combination)
                return
            }

            for i in start..<candidates.count {
                combination.append(candidates[i])
                backtrack(remaining - candidates[i], i, &combination)
                combination.removeLast()
            }
        }

        var combination = [Int]()
        backtrack(target, 0, &combination)
        return result
    }
}

let solution = Solution()
print(solution.combinationSum([2, 3, 6, 7], 7)) // Output: [[2, 2, 3], [7]]
print(solution.combinationSum([2, 3, 5], 8)) // Output: [[2, 2, 2, 2], [2, 3, 3], [3, 5]]
```


### The End

