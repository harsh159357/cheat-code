# Perfect Squares

## Problem Statement

Given an integer `n`, return the least number of perfect square numbers (e.g., `1, 4, 9, 16, ...`) that sum to `n`.

## Input

```text
n = 12
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int numSquares(int n) {
  List<int> dp = List.filled(n + 1, n);

  dp[0] = 0;

  for (int i = 1; i <= n; i++) {
    for (int j = 1; j * j <= i; j++) {
      dp[i] = dp[i].compareTo(dp[i - j * j] + 1) < 0 ? dp[i] : dp[i - j * j] + 1;
    }
  }

  return dp[n];
}
```

### C#

```csharp
public class Solution {
    public int NumSquares(int n) {
        int[] dp = new int[n + 1];
        Array.Fill(dp, int.MaxValue);

        dp[0] = 0;

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j * j <= i; j++) {
                dp[i] = Math.Min(dp[i], dp[i - j * j] + 1);
            }
        }

        return dp[n];
    }
}
```

### Java

```java
class Solution {
    public int numSquares(int n) {
        int[] dp = new int[n + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);

        dp[0] = 0;

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j * j <= i; j++) {
                dp[i] = Math.min(dp[i], dp[i - j * j] + 1);
            }
        }

        return dp[n];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun numSquares(n: Int): Int {
        val dp = IntArray(n + 1) { Int.MAX_VALUE }
        dp[0] = 0

        for (i in 1..n) {
            var j = 1
            while (j * j <= i) {
                dp[i] = minOf(dp[i], dp[i - j * j] + 1)
                j++
            }
        }

        return dp[n]
    }
}
```

### Swift

```swift
class Solution {
    func numSquares(_ n: Int) -> Int {
        var dp = [Int](repeating: Int.max, count: n + 1)
        dp[0] = 0

        for i in 1...n {
            var j = 1
            while j * j <= i {
                dp[i] = min(dp[i], dp[i - j * j] + 1)
                j += 1
            }
        }

        return dp[n]
    }
}
```

### The End

