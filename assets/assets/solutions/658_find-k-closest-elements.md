# Find K Closest Elements

## Problem Statement

Given a sorted integer array `arr`, two integers `k` and `x`, return the `k` closest integers to `x` in the array. The result should also be sorted in ascending order.

The difference between the target value `x` and the closest elements is minimized. If there is a tie, choose the smaller element.

## Input

```text
arr = [1, 2, 3, 4, 5], k = 4, x = 3
```

## Output

```text
[1, 2, 3, 4]
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findClosestElements(arr: IntArray, k: Int, x: Int): List<Int> {
        var left = 0
        var right = arr.size - k

        while (left < right) {
            val mid = left + (right - left) / 2
            if (x - arr[mid] > arr[mid + k] - x) {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return arr.copyOfRange(left, left + k).toList()
    }
}

fun main() {
    val arr = intArrayOf(1, 2, 3, 4, 5)
    val k = 4
    val x = 3
    val solution = Solution()
    println(solution.findClosestElements(arr, k, x)) // Output: [1, 2, 3, 4]
}
```


### Dart

```dart
List<int> findClosestElements(List<int> arr, int k, int x) {
  int left = 0;
  int right = arr.length - k;

  while (left < right) {
    int mid = left + (right - left) ~/ 2;
    if (x - arr[mid] > arr[mid + k] - x) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }

  return arr.sublist(left, left + k);
}

void main() {
  List<int> arr = [1, 2, 3, 4, 5];
  int k = 4;
  int x = 3;
  print(findClosestElements(arr, k, x)); // Output: [1, 2, 3, 4]
}
```


### C#

```csharp
public class Solution {
    public IList<int> FindClosestElements(int[] arr, int k, int x) {
        int left = 0, right = arr.Length - k;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (x - arr[mid] > arr[mid + k] - x) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return arr.Skip(left).Take(k).ToList();
    }
}
```


### Java

```java
import java.util.*;

class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        int left = 0, right = arr.length - k;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (x - arr[mid] > arr[mid + k] - x) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        List<Integer> result = new ArrayList<>();
        for (int i = left; i < left + k; i++) {
            result.add(arr[i]);
        }
        return result;
    }
}
```


### Swift

```swift
class Solution {
    func findClosestElements(_ arr: [Int], _ k: Int, _ x: Int) -> [Int] {
        var left = 0
        var right = arr.count - k

        while left < right {
            let mid = left + (right - left) / 2
            if x - arr[mid] > arr[mid + k] - x {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return Array(arr[left..<left + k])
    }
}

// Example usage
let arr = [1, 2, 3, 4, 5]
let k = 4
let x = 3
let solution = Solution()
print(solution.findClosestElements(arr, k, x)) // Output: [1, 2, 3, 4]
```

### The End