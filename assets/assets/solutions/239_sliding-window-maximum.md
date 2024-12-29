# Sliding Window Maximum

## Problem Statement

You are given an array of integers `nums`, and there is a sliding window of size `k` that moves from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position, return the maximum value of the window.

## Input

```text
nums = [1,3,-1,-3,5,3,6,7], k = 3
```

## Output

```text
[3, 3, 5, 5, 6, 7]
```

## Solutions

### Dart

```dart
List<int> maxSlidingWindow(List<int> nums, int k) {
  List<int> result = [];
  LinkedList<int> deque = LinkedList<int>();

  for (int i = 0; i < nums.length; i++) {
    // Remove indices that are out of the window
    if (deque.isNotEmpty && deque.first == i - k) {
      deque.removeFirst();
    }

    // Remove indices whose values are less than the current value
    while (deque.isNotEmpty && nums[deque.last] < nums[i]) {
      deque.removeLast();
    }

    deque.addLast(i);

    // Add the maximum value of the window to the result
    if (i >= k - 1) {
      result.add(nums[deque.first]);
    }
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public int[] MaxSlidingWindow(int[] nums, int k) {
        LinkedList<int> deque = new LinkedList<int>();
        List<int> result = new List<int>();

        for (int i = 0; i < nums.Length; i++) {
            // Remove indices that are out of the window
            if (deque.Count > 0 && deque.First.Value == i - k) {
                deque.RemoveFirst();
            }

            // Remove indices whose values are less than the current value
            while (deque.Count > 0 && nums[deque.Last.Value] < nums[i]) {
                deque.RemoveLast();
            }

            deque.AddLast(i);

            // Add the maximum value of the window to the result
            if (i >= k - 1) {
                result.Add(nums[deque.First.Value]);
            }
        }

        return result.ToArray();
    }
}
```

### Java

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        LinkedList<Integer> deque = new LinkedList<>();
        int[] result = new int[nums.length - k + 1];
        int index = 0;

        for (int i = 0; i < nums.length; i++) {
            // Remove indices that are out of the window
            if (!deque.isEmpty() && deque.getFirst() == i - k) {
                deque.removeFirst();
            }

            // Remove indices whose values are less than the current value
            while (!deque.isEmpty() && nums[deque.getLast()] < nums[i]) {
                deque.removeLast();
            }

            deque.addLast(i);

            // Add the maximum value of the window to the result
            if (i >= k - 1) {
                result[index++] = nums[deque.getFirst()];
            }
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun maxSlidingWindow(nums: IntArray, k: Int): IntArray {
        val result = IntArray(nums.size - k + 1)
        val deque = LinkedList<Int>()

        for (i in nums.indices) {
            // Remove indices that are out of the window
            if (deque.isNotEmpty() && deque.first == i - k) {
                deque.removeFirst()
            }

            // Remove indices whose values are less than the current value
            while (deque.isNotEmpty() && nums[deque.last] < nums[i]) {
                deque.removeLast()
            }

            deque.addLast(i)

            // Add the maximum value of the window to the result
            if (i >= k - 1) {
                result[i - k + 1] = nums[deque.first]
            }
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func maxSlidingWindow(_ nums: [Int], _ k: Int) -> [Int] {
        var result = [Int]()
        var deque = [Int]()

        for i in 0..<nums.count {
            // Remove indices that are out of the window
            if !deque.isEmpty && deque.first == i - k {
                deque.removeFirst()
            }

            // Remove indices whose values are less than the current value
            while !deque.isEmpty && nums[deque.last!] < nums[i] {
                deque.removeLast()
            }

            deque.append(i)

            // Add the maximum value of the window to the result
            if i >= k - 1 {
                result.append(nums[deque.first!])
            }
        }

        return result
    }
}
```

### The End

