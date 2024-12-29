# Single Number II

## Problem Statement

Given an integer array `nums` where every element appears three times except for one, which appears exactly once. Find the single element and return it.

You must implement a solution with a linear runtime complexity and use only constant extra space.

---

## Input

```text
nums = [2, 2, 3, 2]
```

## Output

```text
3
```


## Solutions

### Dart

```dart
int singleNumber(List<int> nums) {
  int ones = 0, twos = 0;
  for (int num in nums) {
    ones = (ones ^ num) & ~twos;
    twos = (twos ^ num) & ~ones;
  }
  return ones;
}
```


### C#

```csharp
public class Solution {
    public int SingleNumber(int[] nums) {
        int ones = 0, twos = 0;
        foreach (int num in nums) {
            ones = (ones ^ num) & ~twos;
            twos = (twos ^ num) & ~ones;
        }
        return ones;
    }
}
```


### Java

```java
class Solution {
    public int singleNumber(int[] nums) {
        int ones = 0, twos = 0;
        for (int num : nums) {
            ones = (ones ^ num) & ~twos;
            twos = (twos ^ num) & ~ones;
        }
        return ones;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun singleNumber(nums: IntArray): Int {
        var ones = 0
        var twos = 0
        for (num in nums) {
            ones = (ones xor num) and twos.inv()
            twos = (twos xor num) and ones.inv()
        }
        return ones
    }
}
```


### Swift

```swift
class Solution {
    func singleNumber(_ nums: [Int]) -> Int {
        var ones = 0
        var twos = 0
        for num in nums {
            ones = (ones ^ num) & ~twos
            twos = (twos ^ num) & ~ones
        }
        return ones
    }
}
```



### The End

