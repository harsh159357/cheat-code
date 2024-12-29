# Trapping Rain Water

## Problem Statement

Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.

## Input

```text
height = [0,1,0,2,1,0,1,3,2,1,2,1]
```

## Output

```text
6  
(Explanation: The total amount of trapped water is 6 units.)
```

## Solutions

### Dart

```dart
int trap(List<int> height) {
  int left = 0, right = height.length - 1;
  int leftMax = 0, rightMax = 0;
  int waterTrapped = 0;

  while (left < right) {
    if (height[left] < height[right]) {
      if (height[left] >= leftMax) {
        leftMax = height[left];
      } else {
        waterTrapped += leftMax - height[left];
      }
      left++;
    } else {
      if (height[right] >= rightMax) {
        rightMax = height[right];
      } else {
        waterTrapped += rightMax - height[right];
      }
      right--;
    }
  }

  return waterTrapped;
}

void main() {
  print(trap([0,1,0,2,1,0,1,3,2,1,2,1])); // Output: 6
  print(trap([4,2,0,3,2,5])); // Output: 9
}
```

### C#

```csharp
public class Solution {
    public int Trap(int[] height) {
        int left = 0, right = height.Length - 1;
        int leftMax = 0, rightMax = 0;
        int waterTrapped = 0;

        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left];
                } else {
                    waterTrapped += leftMax - height[left];
                }
                left++;
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right];
                } else {
                    waterTrapped += rightMax - height[right];
                }
                right--;
            }
        }

        return waterTrapped;
    }
}
```

### Java

```java
class Solution {
    public int trap(int[] height) {
        int left = 0, right = height.length - 1;
        int leftMax = 0, rightMax = 0;
        int waterTrapped = 0;

        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left];
                } else {
                    waterTrapped += leftMax - height[left];
                }
                left++;
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right];
                } else {
                    waterTrapped += rightMax - height[right];
                }
                right--;
            }
        }

        return waterTrapped;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun trap(height: IntArray): Int {
        var left = 0
        var right = height.size - 1
        var leftMax = 0
        var rightMax = 0
        var waterTrapped = 0

        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left]
                } else {
                    waterTrapped += leftMax - height[left]
                }
                left++
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right]
                } else {
                    waterTrapped += rightMax - height[right]
                }
                right--
            }
        }

        return waterTrapped
    }
}
```

### Swift

```swift
class Solution {
    func trap(_ height: [Int]) -> Int {
        var left = 0, right = height.count - 1
        var leftMax = 0, rightMax = 0
        var waterTrapped = 0

        while left < right {
            if height[left] < height[right] {
                if height[left] >= leftMax {
                    leftMax = height[left]
                } else {
                    waterTrapped += leftMax - height[left]
                }
                left += 1
            } else {
                if height[right] >= rightMax {
                    rightMax = height[right]
                } else {
                    waterTrapped += rightMax - height[right]
                }
                right -= 1
            }
        }

        return waterTrapped
    }
}

let solution = Solution()
print(solution.trap([0,1,0,2,1,0,1,3,2,1,2,1])) // Output: 6
print(solution.trap([4,2,0,3,2,5])) // Output: 9
```


### The End

