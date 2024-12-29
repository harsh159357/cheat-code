# Asteroid Collision

## Problem Statement

We are given an array `asteroids` of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (`positive` meaning right, `negative` meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

## Input

```text
asteroids = [5, 10, -5]
```

## Output

```text
[5, 10]
```

## Solutions

### Dart

```dart
List<int> asteroidCollision(List<int> asteroids) {
  List<int> stack = [];
  for (var asteroid in asteroids) {
    bool destroyed = false;
    while (stack.isNotEmpty && asteroid < 0 && stack.last > 0) {
      if (stack.last + asteroid == 0) {
        stack.removeLast();
        destroyed = true;
        break;
      } else if (stack.last + asteroid < 0) {
        stack.removeLast();
      } else {
        destroyed = true;
        break;
      }
    }
    if (!destroyed) {
      stack.add(asteroid);
    }
  }
  return stack;
}
```

### C#

```csharp
public class Solution {
    public int[] AsteroidCollision(int[] asteroids) {
        var stack = new Stack<int>();
        foreach (int asteroid in asteroids) {
            bool destroyed = false;
            while (stack.Count > 0 && asteroid < 0 && stack.Peek() > 0) {
                if (stack.Peek() + asteroid == 0) {
                    stack.Pop();
                    destroyed = true;
                    break;
                } else if (stack.Peek() + asteroid < 0) {
                    stack.Pop();
                } else {
                    destroyed = true;
                    break;
                }
            }
            if (!destroyed) {
                stack.Push(asteroid);
            }
        }
        return stack.Reverse().ToArray();
    }
}
```

### Java

```java
class Solution {
    public int[] asteroidCollision(int[] asteroids) {
        Stack<Integer> stack = new Stack<>();
        for (int asteroid : asteroids) {
            boolean destroyed = false;
            while (!stack.isEmpty() && asteroid < 0 && stack.peek() > 0) {
                if (stack.peek() + asteroid == 0) {
                    stack.pop();
                    destroyed = true;
                    break;
                } else if (stack.peek() + asteroid < 0) {
                    stack.pop();
                } else {
                    destroyed = true;
                    break;
                }
            }
            if (!destroyed) {
                stack.push(asteroid);
            }
        }
        int[] result = new int[stack.size()];
        for (int i = stack.size() - 1; i >= 0; i--) {
            result[i] = stack.pop();
        }
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun asteroidCollision(asteroids: IntArray): IntArray {
        val stack = mutableListOf<Int>()
        for (ast in asteroids) {
            if (ast > 0) {
                stack.add(ast)
            } else {
                while (stack.isNotEmpty() && stack.last() > 0 && stack.last() < -ast) {
                    stack.removeAt(stack.lastIndex)
                }
                if (stack.isNotEmpty() && stack.last() == -ast) {
                    stack.removeAt(stack.lastIndex)
                } else if (stack.isEmpty() || stack.last() < 0) {
                    stack.add(ast)
                }
            }
        }
        return stack.toIntArray()
    }
}
```

### Swift

```swift
class Solution {
    func asteroidCollision(_ asteroids: [Int]) -> [Int] {
        var stack = [Int]()
        for asteroid in asteroids {
            var destroyed = false
            while let last = stack.last, asteroid < 0 && last > 0 {
                if last + asteroid == 0 {
                    stack.removeLast()
                    destroyed = true
                    break
                } else if last + asteroid < 0 {
                    stack.removeLast()
                } else {
                    destroyed = true
                    break
                }
            }
            if !destroyed {
                stack.append(asteroid)
            }
        }
        return stack
    }
}
```


### The End