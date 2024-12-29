# Climbing Stairs

## Problem Statement

You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Input

```text
n = 3
```

## Output

```text
3  
(Explanation: There are three ways to climb to the top: 1+1+1, 1+2, 2+1.)
```

## Solutions

### Dart

```dart
int climbStairs(int n) {
  if (n <= 2) return n;
  int prev1 = 1, prev2 = 2;

  for (int i = 3; i <= n; i++) {
    int next = prev1 + prev2;
    prev1 = prev2;
    prev2 = next;
  }

  return prev2;
}

void main() {
  print(climbStairs(3)); // Output: 3
  print(climbStairs(5)); // Output: 8
}
```

### C#

```csharp
public class Solution {
    public int ClimbStairs(int n) {
        if (n <= 2) return n;
        int prev1 = 1, prev2 = 2;

        for (int i = 3; i <= n; i++) {
            int next = prev1 + prev2;
            prev1 = prev2;
            prev2 = next;
        }

        return prev2;
    }
}
```

### Java

```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;
        int prev1 = 1, prev2 = 2;

        for (int i = 3; i <= n; i++) {
            int next = prev1 + prev2;
            prev1 = prev2;
            prev2 = next;
        }

        return prev2;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun climbStairs(n: Int): Int {
        if (n <= 2) return n
        var prev1 = 1
        var prev2 = 2

        for (i in 3..n) {
            val next = prev1 + prev2
            prev1 = prev2
            prev2 = next
        }

        return prev2
    }
}
```

### Swift

```swift
class Solution {
    func climbStairs(_ n: Int) -> Int {
        if n <= 2 { return n }
        var prev1 = 1, prev2 = 2

        for _ in 3...n {
            let next = prev1 + prev2
            prev1 = prev2
            prev2 = next
        }

        return prev2
    }
}

let solution = Solution()
print(solution.climbStairs(3)) // Output: 3
print(solution.climbStairs(5)) // Output: 8
```

### The End

