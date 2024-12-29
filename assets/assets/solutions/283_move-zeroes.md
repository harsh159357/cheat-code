# Move Zeroes

## Problem Statement

Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

## Input

```text
nums = [0,1,0,3,12]
```

## Output

```text
[1,3,12,0,0]
```


## Solutions

### Dart

```dart
void moveZeroes(List<int> nums) {
  int i = 0;
  for (int j = 0; j < nums.length; j++) {
    if (nums[j] != 0) {
      nums[i++] = nums[j];
    }
  }
  while (i < nums.length) {
    nums[i++] = 0;
  }
}
```

### C#

```csharp
public class Solution {
    public void MoveZeroes(int[] nums) {
        int i = 0;
        for (int j = 0; j < nums.Length; j++) {
            if (nums[j] != 0) {
                nums[i++] = nums[j];
            }
        }
        while (i < nums.Length) {
            nums[i++] = 0;
        }
    }
}
```

### Java

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int i = 0;
        for (int j = 0; j < nums.length; j++) {
            if (nums[j] != 0) {
                nums[i++] = nums[j];
            }
        }
        while (i < nums.length) {
            nums[i++] = 0;
        }
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun moveZeroes(nums: IntArray) {
        var i = 0
        for (j in nums.indices) {
            if (nums[j] != 0) {
                nums[i++] = nums[j]
            }
        }
        while (i < nums.size) {
            nums[i++] = 0
        }
    }
}
```

### Swift

```swift
class Solution {
    func moveZeroes(_ nums: inout [Int]) {
        var i = 0
        for j in 0..<nums.count {
            if nums[j] != 0 {
                nums[i] = nums[j]
                i += 1
            }
        }
        while i < nums.count {
            nums[i] = 0
            i += 1
        }
    }
}
```

### The End

