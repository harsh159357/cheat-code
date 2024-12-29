# Binary Search

## Problem Statement

Given a sorted array of integers `nums` and a target value `target`, return the index of the target in the array. If the target is not present, return `-1`.

You must write an algorithm with O(log n) runtime complexity.

## Input

nums = [-1, 0, 3, 5, 9, 12]  
target = 9

## Output

4  
(The target 9 is at index 4 in the array.)

## Solutions

### Dart

```dart
int search(List<int> nums, int target) {
  int left = 0;
  int right = nums.length - 1;

  while (left <= right) {
    int mid = left + ((right - left) ~/ 2);

    if (nums[mid] == target) {
      return mid;
    } else if (nums[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }

  return -1;
}

void main() {
  var nums = [-1, 0, 3, 5, 9, 12];
  var target = 9;
  print(search(nums, target)); // Output: 4
}
```

### C#

```csharp
public class Solution {
    public int Search(int[] nums, int target) {
        int left = 0, right = nums.Length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
    }
}

class Program {
    static void Main(string[] args) {
        var solution = new Solution();
        int[] nums = { -1, 0, 3, 5, 9, 12 };
        int target = 9;
        Console.WriteLine(solution.Search(nums, target)); // Output: 4
    }
}
```

### Java

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] nums = { -1, 0, 3, 5, 9, 12 };
        int target = 9;
        System.out.println(solution.search(nums, target)); // Output: 4
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun search(nums: IntArray, target: Int): Int {
        var left = 0
        var right = nums.size - 1
        
        while (left <= right) {
            val mid = left + (right - left) / 2
            
            if (nums[mid] == target) {
                return mid
            } else if (nums[mid] < target) {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }
        
        return -1
    }
}

fun main() {
    val solution = Solution()

    // Example usage
    val nums = intArrayOf(-1, 0, 3, 5, 9, 12)
    val target = 9
    println(solution.search(nums, target)) // Output: 4
}
```

### Swift

```swift
class Solution {
    func search(_ nums: [Int], _ target: Int) -> Int {
        var left = 0
        var right = nums.count - 1

        while left <= right {
            let mid = left + (right - left) / 2

            if nums[mid] == target {
                return mid
            } else if nums[mid] < target {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        return -1
    }
}

let solution = Solution()
let nums = [-1, 0, 3, 5, 9, 12]
let target = 9
print(solution.search(nums, target)) // Output: 4
```

### The End

