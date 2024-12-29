# Subsets

## Problem Statement

Given an integer array `nums` of unique elements, return all possible subsets (the power set).

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

## Input

```text
nums = [1, 2, 3]
```

## Output

```text
[
  [],
  [1],
  [2],
  [3],
  [1, 2],
  [1, 3],
  [2, 3],
  [1, 2, 3]
]
```

## Solutions

### Dart

```dart
List<List<int>> subsets(List<int> nums) {
  List<List<int>> result = [];

  void backtrack(int start, List<int> current) {
    result.add(List.from(current));
    for (int i = start; i < nums.length; i++) {
      current.add(nums[i]);
      backtrack(i + 1, current);
      current.removeLast();
    }
  }

  backtrack(0, []);
  return result;
}

void main() {
  print(subsets([1, 2, 3])); // Output: [[], [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]]
}
```

### C#

```csharp
public class Solution {
    public IList<IList<int>> Subsets(int[] nums) {
        IList<IList<int>> result = new List<IList<int>>();

        void Backtrack(int start, IList<int> current) {
            result.Add(new List<int>(current));
            for (int i = start; i < nums.Length; i++) {
                current.Add(nums[i]);
                Backtrack(i + 1, current);
                current.RemoveAt(current.Count - 1);
            }
        }

        Backtrack(0, new List<int>());
        return result;
    }
}
```

### Java

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] nums, int start, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));
        for (int i = start; i < nums.length; i++) {
            current.add(nums[i]);
            backtrack(nums, i + 1, current, result);
            current.remove(current.size() - 1);
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun subsets(nums: IntArray): List<List<Int>> {
        val result = mutableListOf<List<Int>>()

        fun backtrack(start: Int, current: MutableList<Int>) {
            result.add(current.toList())
            for (i in start until nums.size) {
                current.add(nums[i])
                backtrack(i + 1, current)
                current.removeAt(current.size - 1)
            }
        }

        backtrack(0, mutableListOf())
        return result
    }
}

fun main() {
    val solution = Solution()
    println(solution.subsets(intArrayOf(1, 2, 3))) // Output: [[], [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]]
}
```

### Swift

```swift
class Solution {
    func subsets(_ nums: [Int]) -> [[Int]] {
        var result = [[Int]]()

        func backtrack(_ start: Int, _ current: inout [Int]) {
            result.append(current)
            for i in start..<nums.count {
                current.append(nums[i])
                backtrack(i + 1, &current)
                current.removeLast()
            }
        }

        var current = [Int]()
        backtrack(0, &current)
        return result
    }
}

let solution = Solution()
print(solution.subsets([1, 2, 3])) // Output: [[], [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]]
```


### The End

