# Largest Rectangle in Histogram

## Problem Statement

Given an array of integers `heights` representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

## Input

```text
heights = [2, 1, 5, 6, 2, 3]
```

## Output

```text
10
```

(Explanation: The largest rectangle is formed by the bars of heights 5 and 6, giving an area of `5 * 2 = 10`.)

## Solutions

### Dart

```dart
int largestRectangleArea(List<int> heights) {
  final stack = <int>[];
  int maxArea = 0;
  int i = 0;

  while (i < heights.length) {
    if (stack.isEmpty || heights[i] >= heights[stack.last]) {
      stack.add(i);
      i++;
    } else {
      final topIndex = stack.removeLast();
      final width = stack.isEmpty ? i : i - stack.last - 1;
      maxArea = maxArea > (heights[topIndex] * width) ? maxArea : (heights[topIndex] * width);
    }
  }

  while (stack.isNotEmpty) {
    final topIndex = stack.removeLast();
    final width = stack.isEmpty ? heights.length : heights.length - stack.last - 1;
    maxArea = maxArea > (heights[topIndex] * width) ? maxArea : (heights[topIndex] * width);
  }

  return maxArea;
}

void main() {
  print(largestRectangleArea([2, 1, 5, 6, 2, 3])); // Output: 10
}
```

### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public int LargestRectangleArea(int[] heights) {
        Stack<int> stack = new Stack<int>();
        int maxArea = 0;
        int i = 0;

        while (i < heights.Length) {
            if (stack.Count == 0 || heights[i] >= heights[stack.Peek()]) {
                stack.Push(i);
                i++;
            } else {
                int topIndex = stack.Pop();
                int width = stack.Count == 0 ? i : i - stack.Peek() - 1;
                maxArea = Math.Max(maxArea, heights[topIndex] * width);
            }
        }

        while (stack.Count > 0) {
            int topIndex = stack.Pop();
            int width = stack.Count == 0 ? heights.Length : heights.Length - stack.Peek() - 1;
            maxArea = Math.Max(maxArea, heights[topIndex] * width);
        }

        return maxArea;
    }
}
```

### Java

```java
import java.util.Stack;

class Solution {
    public int largestRectangleArea(int[] heights) {
        Stack<Integer> stack = new Stack<>();
        int maxArea = 0;
        int i = 0;

        while (i < heights.length) {
            if (stack.isEmpty() || heights[i] >= heights[stack.peek()]) {
                stack.push(i);
                i++;
            } else {
                int topIndex = stack.pop();
                int width = stack.isEmpty() ? i : i - stack.peek() - 1;
                maxArea = Math.max(maxArea, heights[topIndex] * width);
            }
        }

        while (!stack.isEmpty()) {
            int topIndex = stack.pop();
            int width = stack.isEmpty() ? heights.length : heights.length - stack.peek() - 1;
            maxArea = Math.max(maxArea, heights[topIndex] * width);
        }

        return maxArea;
    }
}
```

### Kotlin

```kotlin
import java.util.Stack

class Solution {
    fun largestRectangleArea(heights: IntArray): Int {
        val stack = Stack<Int>()
        var maxArea = 0
        var i = 0

        while (i < heights.size) {
            if (stack.isEmpty() || heights[i] >= heights[stack.peek()]) {
                stack.push(i)
                i++
            } else {
                val topIndex = stack.pop()
                val width = if (stack.isEmpty()) i else i - stack.peek() - 1
                maxArea = maxOf(maxArea, heights[topIndex] * width)
            }
        }

        while (stack.isNotEmpty()) {
            val topIndex = stack.pop()
            val width = if (stack.isEmpty()) heights.size else heights.size - stack.peek() - 1
            maxArea = maxOf(maxArea, heights[topIndex] * width)
        }

        return maxArea
    }
}

fun main() {
    val solution = Solution()
    println(solution.largestRectangleArea(intArrayOf(2, 1, 5, 6, 2, 3))) // Output: 10
}
```

### Swift

```swift
class Solution {
    func largestRectangleArea(_ heights: [Int]) -> Int {
        var stack = [Int]()
        var maxArea = 0
        var i = 0

        while i < heights.count {
            if stack.isEmpty || heights[i] >= heights[stack.last!] {
                stack.append(i)
                i += 1
            } else {
                let topIndex = stack.removeLast()
                let width = stack.isEmpty ? i : i - stack.last! - 1
                maxArea = max(maxArea, heights[topIndex] * width)
            }
        }

        while !stack.isEmpty {
            let topIndex = stack.removeLast()
            let width = stack.isEmpty ? heights.count : heights.count - stack.last! - 1
            maxArea = max(maxArea, heights[topIndex] * width)
        }

        return maxArea
    }
}

let solution = Solution()
print(solution.largestRectangleArea([2, 1, 5, 6, 2, 3])) // Output: 10
```

### The End

