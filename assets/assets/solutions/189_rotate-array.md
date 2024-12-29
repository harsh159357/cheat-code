Here is the improved content, strictly adhering to the required structure:

---

# Rotate Array

## Problem Statement

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

## Input

```text
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

## Output

```text
[5, 6, 7, 1, 2, 3, 4]
```


## Solutions

### Dart

```dart
void rotate(List<int> nums, int k) {
  int n = nums.length;
  int steps = k % n;

  reverse(nums, 0, n - 1);
  reverse(nums, 0, steps - 1);
  reverse(nums, steps, n - 1);
}

void reverse(List<int> nums, int start, int end) {
  while (start < end) {
    int temp = nums[start];
    nums[start] = nums[end];
    nums[end] = temp;
    start++;
    end--;
  }
}
```


### C#

```csharp
public class Solution {
    public void Rotate(int[] nums, int k) {
        int n = nums.Length;
        k %= n;

        Reverse(nums, 0, n - 1);
        Reverse(nums, 0, k - 1);
        Reverse(nums, k, n - 1);
    }

    private void Reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```


### Java

```java
class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k %= n;

        reverse(nums, 0, n - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, n - 1);
    }

    private void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun rotate(nums: IntArray, k: Int) {
        val n = nums.size
        val steps = k % n

        reverse(nums, 0, n - 1)
        reverse(nums, 0, steps - 1)
        reverse(nums, steps, n - 1)
    }

    private fun reverse(nums: IntArray, start: Int, end: Int) {
        var left = start
        var right = end
        while (left < right) {
            val temp = nums[left]
            nums[left] = nums[right]
            nums[right] = temp
            left++
            right--
        }
    }
}
```


### Swift

```swift
class Solution {
    func rotate(_ nums: inout [Int], _ k: Int) {
        let n = nums.count
        let steps = k % n

        reverse(&nums, 0, n - 1)
        reverse(&nums, 0, steps - 1)
        reverse(&nums, steps, n - 1)
    }

    private func reverse(_ nums: inout [Int], _ start: Int, _ end: Int) {
        var start = start, end = end
        while start < end {
            nums.swapAt(start, end)
            start += 1
            end -= 1
        }
    }
}
```


### The End

