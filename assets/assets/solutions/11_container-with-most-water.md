# Container With Most Water

## Problem Statement

Given an integer array `height` of length `n`, where `n` represents the heights of vertical lines, find two lines that together with the x-axis form a container that holds the most water.

Return the maximum amount of water a container can store.

## Input

```text
height = [1, 8, 6, 2, 5, 4, 8, 3, 7]
```

## Output

```text
49  
(Explanation: The maximum area is formed by lines at indices 1 and 8, with a height of 7 and a width of 7.)
```

## Solutions

### Dart

```dart
int maxArea(List<int> height) {
  int maxArea = 0;
  int left = 0;
  int right = height.length - 1;

  while (left < right) {
    int minHeight = height[left] < height[right] ? height[left] : height[right];
    int currentArea = minHeight * (right - left);
    maxArea = maxArea > currentArea ? maxArea : currentArea;

    if (height[left] < height[right]) {
      left++;
    } else {
      right--;
    }
  }

  return maxArea;
}

void main() {
  print(maxArea([1, 8, 6, 2, 5, 4, 8, 3, 7])); // Output: 49
  print(maxArea([1, 1])); // Output: 1
}
```

### C#

```csharp
public class Solution {
    public int MaxArea(int[] height) {
        int maxArea = 0;
        int left = 0, right = height.Length - 1;

        while (left < right) {
            int minHeight = Math.Min(height[left], height[right]);
            int currentArea = minHeight * (right - left);
            maxArea = Math.Max(maxArea, currentArea);

            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }
}
```

### Java

```java
class Solution {
    public int maxArea(int[] height) {
        int maxArea = 0;
        int left = 0, right = height.length - 1;

        while (left < right) {
            int minHeight = Math.min(height[left], height[right]);
            int currentArea = minHeight * (right - left);
            maxArea = Math.max(maxArea, currentArea);

            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun maxArea(height: IntArray): Int {
        var maxArea = 0
        var left = 0
        var right = height.size - 1

        while (left < right) {
            val minHeight = minOf(height[left], height[right])
            val currentArea = minHeight * (right - left)
            maxArea = maxOf(maxArea, currentArea)

            if (height[left] < height[right]) {
                left++
            } else {
                right--
            }
        }

        return maxArea
    }
}

fun main() {
    val height1 = intArrayOf(1, 8, 6, 2, 5, 4, 8, 3, 7)
    println(Solution().maxArea(height1)) // Output: 49

    val height2 = intArrayOf(1, 1)
    println(Solution().maxArea(height2)) // Output: 1
}
```

### Swift

```swift
class Solution {
    func maxArea(_ height: [Int]) -> Int {
        var maxArea = 0
        var left = 0
        var right = height.count - 1

        while left < right {
            let minHeight = min(height[left], height[right])
            let currentArea = minHeight * (right - left)
            maxArea = max(maxArea, currentArea)

            if height[left] < height[right] {
                left += 1
            } else {
                right -= 1
            }
        }

        return maxArea
    }
}

let solution = Solution()
print(solution.maxArea([1, 8, 6, 2, 5, 4, 8, 3, 7])) // Output: 49
print(solution.maxArea([1, 1])) // Output: 1
```

### The End

