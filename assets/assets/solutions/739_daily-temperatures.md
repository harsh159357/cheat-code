# Daily Temperatures

## Problem Statement

Given a list of daily temperatures `T`, return a list such that, for each day in the input, it tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put `0` instead.

## Input

```text
T = [73, 74, 75, 71, 69, 72, 76, 73]
```

## Output

```text
[1, 1, 4, 2, 1, 1, 0, 0]
```

## Solutions

### Dart

```dart
List<int> dailyTemperatures(List<int> T) {
  List<int> result = List.filled(T.length, 0);
  List<int> stack = [];

  for (int i = 0; i < T.length; i++) {
    while (stack.isNotEmpty && T[i] > T[stack.last]) {
      int idx = stack.removeLast();
      result[idx] = i - idx;
    }
    stack.add(i);
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public int[] DailyTemperatures(int[] T) {
        int[] result = new int[T.Length];
        Stack<int> stack = new Stack<int>();

        for (int i = 0; i < T.Length; i++) {
            while (stack.Count > 0 && T[i] > T[stack.Peek()]) {
                int idx = stack.Pop();
                result[idx] = i - idx;
            }
            stack.Push(i);
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public int[] dailyTemperatures(int[] T) {
        int[] result = new int[T.length];
        Stack<Integer> stack = new Stack<>();

        for (int i = 0; i < T.length; i++) {
            while (!stack.isEmpty() && T[i] > T[stack.peek()]) {
                int idx = stack.pop();
                result[idx] = i - idx;
            }
            stack.push(i);
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun dailyTemperatures(T: IntArray): IntArray {
        val result = IntArray(T.size)
        val stack = java.util.Stack<Int>()

        for (i in T.indices) {
            while (stack.isNotEmpty() && T[i] > T[stack.peek()]) {
                val idx = stack.pop()
                result[idx] = i - idx
            }
            stack.push(i)
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func dailyTemperatures(_ T: [Int]) -> [Int] {
        var result = Array(repeating: 0, count: T.count)
        var stack = [Int]()

        for i in T.indices {
            while let last = stack.last, T[i] > T[last] {
                let idx = stack.removeLast()
                result[idx] = i - idx
            }
            stack.append(i)
        }

        return result
    }
}
```


### The End