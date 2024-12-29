# Maximum Product Subarray

## Problem Statement

Given an integer array `nums`, find a contiguous non-empty subarray within the array that has the largest product, and return the product.

A subarray is a contiguous subsequence of the array.

---

## Input

```text
nums = [2, 3, -2, 4]
```


## Output

```text
6
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxProduct(nums: IntArray): Int {
        if (nums.isEmpty()) return 0
        
        var prevMin = 1
        var prevMax = 1
        var maxProduct = Int.MIN_VALUE
        
        for (num in nums) {
            val curMin = minOf(num, prevMin * num, prevMax * num)
            val curMax = maxOf(num, prevMin * num, prevMax * num)

            maxProduct = maxOf(maxProduct, curMax)
            
            prevMin = curMin
            prevMax = curMax
        }
        
        return maxProduct
    }
}
```


### Dart

```dart
int maxProduct(List<int> nums) {
  if (nums.isEmpty) return 0;

  int prevMin = 1, prevMax = 1, maxProduct = nums[0];

  for (var num in nums) {
    final curMin = [num, prevMin * num, prevMax * num].reduce((a, b) => a < b ? a : b);
    final curMax = [num, prevMin * num, prevMax * num].reduce((a, b) => a > b ? a : b);

    maxProduct = maxProduct > curMax ? maxProduct : curMax;

    prevMin = curMin;
    prevMax = curMax;
  }

  return maxProduct;
}
```


### C#

```csharp
public class Solution {
    public int MaxProduct(int[] nums) {
        if (nums.Length == 0) return 0;

        int prevMin = 1, prevMax = 1, maxProduct = int.MinValue;

        foreach (var num in nums) {
            int curMin = Math.Min(num, Math.Min(prevMin * num, prevMax * num));
            int curMax = Math.Max(num, Math.Max(prevMin * num, prevMax * num));

            maxProduct = Math.Max(maxProduct, curMax);

            prevMin = curMin;
            prevMax = curMax;
        }

        return maxProduct;
    }
}
```


### Java

```java
class Solution {
    public int maxProduct(int[] nums) {
        if (nums.length == 0) return 0;

        int prevMin = 1, prevMax = 1, maxProduct = Integer.MIN_VALUE;

        for (int num : nums) {
            int curMin = Math.min(num, Math.min(prevMin * num, prevMax * num));
            int curMax = Math.max(num, Math.max(prevMin * num, prevMax * num));

            maxProduct = Math.max(maxProduct, curMax);

            prevMin = curMin;
            prevMax = curMax;
        }

        return maxProduct;
    }
}
```


### Swift

```swift
class Solution {
    func maxProduct(_ nums: [Int]) -> Int {
        if nums.isEmpty { return 0 }

        var prevMin = 1
        var prevMax = 1
        var maxProduct = Int.min

        for num in nums {
            let curMin = min(num, prevMin * num, prevMax * num)
            let curMax = max(num, prevMin * num, prevMax * num)

            maxProduct = max(maxProduct, curMax)

            prevMin = curMin
            prevMax = curMax
        }

        return maxProduct
    }
}
```



### The End

