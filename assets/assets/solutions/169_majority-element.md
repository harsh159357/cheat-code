# Majority Element

## Problem Statement

Given an array `nums` of size `n`, return the majority element.  
The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

---

## Input

```text
nums = [3,2,3]
```

---

## Output

```text
3
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun majorityElement(nums: IntArray): Int {
        var count = 0
        var candidate = 0
        
        for (num in nums) {
            if (count == 0) {
                candidate = num
            }
            count += if (num == candidate) 1 else -1
        }
        
        return candidate
    }
}
```

### Dart

```dart
int majorityElement(List<int> nums) {
  int count = 0;
  int candidate = 0;

  for (int num in nums) {
    if (count == 0) {
      candidate = num;
    }
    count += (num == candidate) ? 1 : -1;
  }

  return candidate;
}
```

### C#

```csharp
public class Solution {
    public int MajorityElement(int[] nums) {
        int count = 0;
        int candidate = 0;

        foreach (int num in nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }

        return candidate;
    }
}
```

### Java

```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int candidate = 0;

        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }

        return candidate;
    }
}
```


### Swift

```swift
class Solution {
    func majorityElement(_ nums: [Int]) -> Int {
        var count = 0
        var candidate = 0

        for num in nums {
            if count == 0 {
                candidate = num
            }
            count += (num == candidate) ? 1 : -1
        }

        return candidate
    }
}
```



### The End

