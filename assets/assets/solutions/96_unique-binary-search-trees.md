# Unique Binary Search Trees

## Problem Statement

Given an integer `n`, return the number of structurally unique BST's (binary search trees) which have exactly `n` nodes of unique values from `1` to `n`.

## Input

```text
n = 3
```

## Output

```text
5
```

## Solutions

### Dart

```dart
int numTrees(int n) {
  List<int> dp = List.filled(n + 1, 0);
  dp[0] = 1;
  dp[1] = 1;

  for (int i = 2; i <= n; i++) {
    for (int root = 1; root <= i; root++) {
      dp[i] += dp[root - 1] * dp[i - root];
    }
  }
  return dp[n];
}
```

### C#

```csharp
public class Solution {
    public int NumTrees(int n) {
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;

        for (int i = 2; i <= n; i++) {
            for (int root = 1; root <= i; root++) {
                dp[i] += dp[root - 1] * dp[i - root];
            }
        }
        return dp[n];
    }
}
```

### Java

```java
class Solution {
    public int numTrees(int n) {
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;

        for (int i = 2; i <= n; i++) {
            for (int root = 1; root <= i; root++) {
                dp[i] += dp[root - 1] * dp[i - root];
            }
        }
        return dp[n];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun numTrees(n: Int): Int {
        val dp = IntArray(n + 1)
        dp[0] = 1
        dp[1] = 1

        for (i in 2..n) {
            for (root in 1..i) {
                dp[i] += dp[root - 1] * dp[i - root]
            }
        }
        return dp[n]
    }
}
```

### Swift

```swift
class Solution {
    func numTrees(_ n: Int) -> Int {
        var dp = [Int](repeating: 0, count: n + 1)
        dp[0] = 1
        dp[1] = 1

        for i in 2...n {
            for root in 1...i {
                dp[i] += dp[root - 1] * dp[i - root]
            }
        }
        return dp[n]
    }
}
```

### The End

