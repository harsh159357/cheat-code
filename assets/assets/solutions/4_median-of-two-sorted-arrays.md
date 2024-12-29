# Median of Two Sorted Arrays

## Problem Statement

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

## Input

```text
nums1 = [1, 3]  
nums2 = [2]
```

## Output

```text
2.0  
(Explanation: The merged array is [1, 2, 3] and the median is 2.0.)
```

## Solutions

### Dart

```dart
double findMedianSortedArrays(List<int> nums1, List<int> nums2) {
  if (nums1.length > nums2.length) {
    return findMedianSortedArrays(nums2, nums1);
  }

  int m = nums1.length;
  int n = nums2.length;
  int left = 0, right = m;
  int halfLen = (m + n + 1) ~/ 2;

  while (left <= right) {
    int partitionX = (left + right) ~/ 2;
    int partitionY = halfLen - partitionX;

    int maxX = (partitionX == 0) ? double.negativeInfinity.toInt() : nums1[partitionX - 1];
    int minX = (partitionX == m) ? double.infinity.toInt() : nums1[partitionX];

    int maxY = (partitionY == 0) ? double.negativeInfinity.toInt() : nums2[partitionY - 1];
    int minY = (partitionY == n) ? double.infinity.toInt() : nums2[partitionY];

    if (maxX <= minY && maxY <= minX) {
      if ((m + n) % 2 == 0) {
        return (max(maxX, maxY) + min(minX, minY)) / 2.0;
      } else {
        return max(maxX, maxY).toDouble();
      }
    } else if (maxX > minY) {
      right = partitionX - 1;
    } else {
      left = partitionX + 1;
    }
  }

  return 0.0;
}
```

### C#

```csharp
public class Solution {
    public double FindMedianSortedArrays(int[] nums1, int[] nums2) {
        if (nums1.Length > nums2.Length) {
            return FindMedianSortedArrays(nums2, nums1);
        }

        int m = nums1.Length;
        int n = nums2.Length;
        int left = 0, right = m;
        int halfLen = (m + n + 1) / 2;

        while (left <= right) {
            int partitionX = (left + right) / 2;
            int partitionY = halfLen - partitionX;

            int maxX = (partitionX == 0) ? int.MinValue : nums1[partitionX - 1];
            int minX = (partitionX == m) ? int.MaxValue : nums1[partitionX];

            int maxY = (partitionY == 0) ? int.MinValue : nums2[partitionY - 1];
            int minY = (partitionY == n) ? int.MaxValue : nums2[partitionY];

            if (maxX <= minY && maxY <= minX) {
                if ((m + n) % 2 == 0) {
                    return (Math.Max(maxX, maxY) + Math.Min(minX, minY)) / 2.0;
                } else {
                    return Math.Max(maxX, maxY);
                }
            } else if (maxX > minY) {
                right = partitionX - 1;
            } else {
                left = partitionX + 1;
            }
        }

        return 0.0;
    }
}
```

### Java

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        if (nums1.length > nums2.length) {
            return findMedianSortedArrays(nums2, nums1);
        }

        int m = nums1.length;
        int n = nums2.length;
        int left = 0, right = m;
        int halfLen = (m + n + 1) / 2;

        while (left <= right) {
            int partitionX = (left + right) / 2;
            int partitionY = halfLen - partitionX;

            int maxX = (partitionX == 0) ? Integer.MIN_VALUE : nums1[partitionX - 1];
            int minX = (partitionX == m) ? Integer.MAX_VALUE : nums1[partitionX];

            int maxY = (partitionY == 0) ? Integer.MIN_VALUE : nums2[partitionY - 1];
            int minY = (partitionY == n) ? Integer.MAX_VALUE : nums2[partitionY];

            if (maxX <= minY && maxY <= minX) {
                if ((m + n) % 2 == 0) {
                    return (Math.max(maxX, maxY) + Math.min(minX, minY)) / 2.0;
                } else {
                    return Math.max(maxX, maxY);
                }
            } else if (maxX > minY) {
                right = partitionX - 1;
            } else {
                left = partitionX + 1;
            }
        }

        return 0.0;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun findMedianSortedArrays(nums1: IntArray, nums2: IntArray): Double {
        val m = nums1.size
        val n = nums2.size
        if (m > n) return findMedianSortedArrays(nums2, nums1)
        var left = 0
        var right = m
        val halfLen = (m + n + 1) / 2
        while (left <= right) {
            val partitionX = left + (right - left) / 2
            val partitionY = halfLen - partitionX
            val maxX = if (partitionX == 0) Int.MIN_VALUE else nums1[partitionX - 1]
            val minX = if (partitionX == m) Int.MAX_VALUE else nums1[partitionX]
            val maxY = if (partitionY == 0) Int.MIN_VALUE else nums2[partitionY - 1]
            val minY = if (partitionY == n) Int.MAX_VALUE else nums2[partitionY]
            if (maxX <= minY && maxY <= minX) {
                if ((m + n) % 2 == 0) {
                    return (maxOf(maxX, maxY) + minOf(minX, minY)) / 2.0
                } else {
                    return maxOf(maxX, maxY).toDouble()
                }
            } else if (maxX > minY) {
                right = partitionX - 1
            } else {
                left = partitionX + 1
            }
        }
        return 0.0
    }
}
```

### Swift

```swift
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
        if nums1.count > nums2.count {
            return findMedianSortedArrays(nums2, nums1)
        }

        let m = nums1.count
        let n = nums2.count
        var left = 0
        var right = m
        let halfLen = (m + n + 1) / 2

        while left <= right {
            let partitionX = (left + right) / 2
            let partitionY = halfLen - partitionX

            let maxX = (partitionX == 0) ? Int.min : nums1[partitionX - 1]
            let minX = (partitionX == m) ? Int.max : nums1[partitionX]

            let maxY = (partitionY == 0) ? Int.min : nums2[partitionY - 1]
            let minY = (partitionY == n) ? Int.max : nums2[partitionY]

            if maxX <= minY && maxY <= minX {
                if (m + n) % 2 == 0 {
                    return Double(max(maxX, maxY) + min(minX, minY)) / 2.0
                } else {
                    return Double(max(maxX, maxY))
                }
            } else if maxX > minY {
                right = partitionX - 1
            } else {
                left = partitionX + 1
            }
        }

        return 0.0
    }
}
```

### The End

