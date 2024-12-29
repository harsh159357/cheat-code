# Product of Array Except Self

## Problem Statement

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

The algorithm should run in `O(n)` time and not use division.

## Input

```text
nums = [1, 2, 3, 4]
```

## Output

```text
[24, 12, 8, 6]
```

## Solutions

### Dart

```dart
List<int> productExceptSelf(List<int> nums) {
  int n = nums.length;
  List<int> result = List.filled(n, 1);

  int prefix = 1;
  for (int i = 0; i < n; i++) {
    result[i] *= prefix;
    prefix *= nums[i];
  }

  int suffix = 1;
  for (int i = n - 1; i >= 0; i--) {
    result[i] *= suffix;
    suffix *= nums[i];
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public int[] ProductExceptSelf(int[] nums) {
        int n = nums.Length;
        int[] result = new int[n];
        Array.Fill(result, 1);

        int prefix = 1;
        for (int i = 0; i < n; i++) {
            result[i] *= prefix;
            prefix *= nums[i];
        }

        int suffix = 1;
        for (int i = n - 1; i >= 0; i--) {
            result[i] *= suffix;
            suffix *= nums[i];
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        Arrays.fill(result, 1);

        int prefix = 1;
        for (int i = 0; i < n; i++) {
            result[i] *= prefix;
            prefix *= nums[i];
        }

        int suffix = 1;
        for (int i = n - 1; i >= 0; i--) {
            result[i] *= suffix;
            suffix *= nums[i];
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun productExceptSelf(nums: IntArray): IntArray {
        val n = nums.size
        val result = IntArray(n) { 1 }

        var prefix = 1
        for (i in 0 until n) {
            result[i] *= prefix
            prefix *= nums[i]
        }

        var suffix = 1
        for (i in n - 1 downTo 0) {
            result[i] *= suffix
            suffix *= nums[i]
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func productExceptSelf(_ nums: [Int]) -> [Int] {
        let n = nums.count
        var result = Array(repeating: 1, count: n)

        var prefix = 1
        for i in 0..<n {
            result[i] *= prefix
            prefix *= nums[i]
        }

        var suffix = 1
        for i in (0..<n).reversed() {
            result[i] *= suffix
            suffix *= nums[i]
        }

        return result
    }
}
```

### The End

