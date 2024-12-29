# Two Sum II - Input Array Is Sorted

## Problem Statement

Given a **1-indexed** array of integers `numbers` that is already sorted in non-decreasing order, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return the indices of the two numbers, `index1` and `index2`, added by one as an integer array `[index1, index2]`.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice.

The solution must use only constant extra space.

---

## Input

```text
numbers = [2,7,11,15], target = 9
```

---

## Output

```text
[1, 2]
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun twoSum(numbers: IntArray, target: Int): IntArray {
        var left = 0
        var right = numbers.size - 1

        while (left < right) {
            val sum = numbers[left] + numbers[right]
            when {
                sum == target -> return intArrayOf(left + 1, right + 1)
                sum < target -> left++
                else -> right--
            }
        }

        return intArrayOf(-1, -1)
    }
}
```


### Dart

```dart
List<int> twoSum(List<int> numbers, int target) {
  int left = 0;
  int right = numbers.length - 1;

  while (left < right) {
    int sum = numbers[left] + numbers[right];
    if (sum == target) {
      return [left + 1, right + 1];
    } else if (sum < target) {
      left++;
    } else {
      right--;
    }
  }

  return [-1, -1];
}
```


### C#

```csharp
public class Solution {
    public int[] TwoSum(int[] numbers, int target) {
        int left = 0, right = numbers.Length - 1;

        while (left < right) {
            int sum = numbers[left] + numbers[right];
            if (sum == target) {
                return new int[] { left + 1, right + 1 };
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }

        return new int[] { -1, -1 };
    }
}
```


### Java

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left = 0, right = numbers.length - 1;

        while (left < right) {
            int sum = numbers[left] + numbers[right];
            if (sum == target) {
                return new int[] { left + 1, right + 1 };
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }

        return new int[] { -1, -1 };
    }
}
```


### Swift

```swift
class Solution {
    func twoSum(_ numbers: [Int], _ target: Int) -> [Int] {
        var left = 0
        var right = numbers.count - 1

        while left < right {
            let sum = numbers[left] + numbers[right]
            if sum == target {
                return [left + 1, right + 1]
            } else if sum < target {
                left += 1
            } else {
                right -= 1
            }
        }

        return [-1, -1]
    }
}
```

### The End

