# Sign of the Product of an Array

## Problem Statement

Given an integer array `nums`, return the **sign** of the product of all values in the array.
- If the product is positive, return `1`.
- If the product is negative, return `-1`.
- If the product is `0`, return `0`.

You must not use the actual product of the array as it may be too large.

## Input

```text
nums = [-1, -2, -3, -4, 3, 2, 1]
```

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun arraySign(nums: IntArray): Int {
        var negativeCount = 0
        for (num in nums) {
            if (num == 0) return 0
            if (num < 0) negativeCount++
        }
        return if (negativeCount % 2 == 0) 1 else -1
    }
}

fun main() {
    val nums = intArrayOf(-1, -2, -3, -4, 3, 2, 1)
    println(Solution().arraySign(nums)) // Output: 1
}
```

### Dart

```dart
int arraySign(List<int> nums) {
  int negativeCount = 0;
  for (int num in nums) {
    if (num == 0) return 0;
    if (num < 0) negativeCount++;
  }
  return (negativeCount % 2 == 0) ? 1 : -1;
}

void main() {
  List<int> nums = [-1, -2, -3, -4, 3, 2, 1];
  print(arraySign(nums)); // Output: 1
}
```

### C#

```csharp
public class Solution {
    public int ArraySign(int[] nums) {
        int negativeCount = 0;
        foreach (int num in nums) {
            if (num == 0) return 0;
            if (num < 0) negativeCount++;
        }
        return (negativeCount % 2 == 0) ? 1 : -1;
    }
}
```

### Java

```java
class Solution {
    public int arraySign(int[] nums) {
        int negativeCount = 0;
        for (int num : nums) {
            if (num == 0) return 0;
            if (num < 0) negativeCount++;
        }
        return (negativeCount % 2 == 0) ? 1 : -1;
    }
}
```

### Swift

```swift
class Solution {
    func arraySign(_ nums: [Int]) -> Int {
        var negativeCount = 0
        for num in nums {
            if num == 0 { return 0 }
            if num < 0 { negativeCount += 1 }
        }
        return negativeCount % 2 == 0 ? 1 : -1
    }
}

let nums = [-1, -2, -3, -4, 3, 2, 1]
print(Solution().arraySign(nums)) // Output: 1
```

### The End