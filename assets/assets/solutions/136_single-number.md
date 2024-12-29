# Single Number

## Problem Statement

Given a non-empty array of integers `nums`, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

---

## Input

```text
nums = [4, 1, 2, 1, 2]
```

## Output

```text
4
```


## Solutions

### Dart

```dart
int singleNumber(List<int> nums) {
  int result = 0;
  for (int num in nums) {
    result ^= num;
  }
  return result;
}
```


### C#

```csharp
public class Solution {
    public int SingleNumber(int[] nums) {
        int result = 0;
        foreach (int num in nums) {
            result ^= num;
        }
        return result;
    }
}
```


### Java

```java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num;
        }
        return result;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun singleNumber(nums: IntArray): Int {
        var result = 0
        for (num in nums) {
            result = result xor num
        }
        return result
    }
}
```


### Swift

```swift
class Solution {
    func singleNumber(_ nums: [Int]) -> Int {
        var result = 0
        for num in nums {
            result ^= num
        }
        return result
    }
}
```


### The End

