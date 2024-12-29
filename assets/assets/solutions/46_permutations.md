# Permutations

## Problem Statement

Given an array `nums` of distinct integers, return all the possible permutations. You can return the answer in any order.

## Input

```text
nums = [1,2,3]
```

## Output

```text
[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]  
(Explanation: These are all the possible arrangements of the array `[1, 2, 3]`.)
```

## Solutions

### Dart

```dart
List<List<int>> permute(List<int> nums) {
  List<List<int>> result = [];

  void backtrack(List<int> nums, List<int> permutation) {
    if (nums.isEmpty) {
      result.add(List.from(permutation));
      return;
    }

    for (int i = 0; i < nums.length; i++) {
      int num = nums[i];
      permutation.add(num);
      nums.removeAt(i);
      backtrack(nums, permutation);
      nums.insert(i, num);
      permutation.removeLast();
    }
  }

  backtrack(nums, []);
  return result;
}

void main() {
  print(permute([1, 2, 3])); // Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
}
```

### C#

```csharp
public class Solution {
    public IList<IList<int>> Permute(int[] nums) {
        IList<IList<int>> result = new List<IList<int>>();

        void Backtrack(List<int> nums, List<int> permutation) {
            if (nums.Count == 0) {
                result.Add(new List<int>(permutation));
                return;
            }

            for (int i = 0; i < nums.Count; i++) {
                int num = nums[i];
                permutation.Add(num);
                nums.RemoveAt(i);
                Backtrack(nums, permutation);
                nums.Insert(i, num);
                permutation.RemoveAt(permutation.Count - 1);
            }
        }

        Backtrack(new List<int>(nums), new List<int>());
        return result;
    }
}
```

### Java

```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();

        void backtrack(List<Integer> nums, List<Integer> permutation) {
            if (nums.isEmpty()) {
                result.add(new ArrayList<>(permutation));
                return;
            }

            for (int i = 0; i < nums.size(); i++) {
                int num = nums.remove(i);
                permutation.add(num);
                backtrack(nums, permutation);
                nums.add(i, num);
                permutation.remove(permutation.size() - 1);
            }
        }

        backtrack(new ArrayList<>(Arrays.asList(nums)), new ArrayList<>());
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun permute(nums: IntArray): List<List<Int>> {
        val result = mutableListOf<List<Int>>()

        fun backtrack(nums: MutableList<Int>, permutation: MutableList<Int>) {
            if (nums.isEmpty()) {
                result.add(ArrayList(permutation))
                return
            }
            for (i in nums.indices) {
                val num = nums[i]
                permutation.add(num)
                nums.removeAt(i)
                backtrack(nums, permutation)
                nums.add(i, num)
                permutation.removeAt(permutation.size - 1)
            }
        }

        backtrack(nums.toMutableList(), mutableListOf())
        return result
    }
}
```

### Swift

```swift
class Solution {
    func permute(_ nums: [Int]) -> [[Int]] {
        var result = [[Int]]()

        func backtrack(_ nums: inout [Int], _ permutation: inout [Int]) {
            if nums.isEmpty {
                result.append(permutation)
                return
            }

            for i in 0..<nums.count {
                let num = nums.remove(at: i)
                permutation.append(num)
                backtrack(&nums, &permutation)
                nums.insert(num, at: i)
                permutation.removeLast()
            }
        }

        var numsCopy = nums
        var permutation = [Int]()
        backtrack(&numsCopy, &permutation)
        return result
    }
}

let solution = Solution()
print(solution.permute([1, 2, 3])) // Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```


### The End

