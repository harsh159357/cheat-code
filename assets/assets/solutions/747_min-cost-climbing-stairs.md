# Min Cost Climbing Stairs

## Problem Statement

You are given an integer array `cost` where `cost[i]` is the cost of the `i`-th step on a staircase. Once you pay the cost, you can either climb one or two steps.

Return the minimum cost to reach the top of the floor.

## Input

```text
cost = [10, 15, 20]
```

## Output

```text
15
```

## Solutions

### Dart

```dart
int minCostClimbingStairs(List<int> cost) {
  int n = cost.length;
  List<int> dp = List.filled(n, 0);

  dp[0] = cost[0];
  dp[1] = cost[1];

  for (int i = 2; i < n; i++) {
    dp[i] = cost[i] + (dp[i - 1] < dp[i - 2] ? dp[i - 1] : dp[i - 2]);
  }

  return dp[n - 1] < dp[n - 2] ? dp[n - 1] : dp[n - 2];
}
```

### C#

```csharp
public class Solution {
    public int MinCostClimbingStairs(int[] cost) {
        int n = cost.Length;
        int[] dp = new int[n];

        dp[0] = cost[0];
        dp[1] = cost[1];

        for (int i = 2; i < n; i++) {
            dp[i] = cost[i] + Math.Min(dp[i - 1], dp[i - 2]);
        }

        return Math.Min(dp[n - 1], dp[n - 2]);
    }
}
```

### Java

```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int n = cost.length;
        int[] dp = new int[n];

        dp[0] = cost[0];
        dp[1] = cost[1];

        for (int i = 2; i < n; i++) {
            dp[i] = cost[i] + Math.min(dp[i - 1], dp[i - 2]);
        }

        return Math.min(dp[n - 1], dp[n - 2]);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun minCostClimbingStairs(cost: IntArray): Int {
        val n = cost.size
        val dp = IntArray(n)

        dp[0] = cost[0]
        dp[1] = cost[1]

        for (i in 2 until n) {
            dp[i] = cost[i] + minOf(dp[i - 1], dp[i - 2])
        }

        return minOf(dp[n - 1], dp[n - 2])
    }
}
```

### Swift

```swift
class Solution {
    func minCostClimbingStairs(_ cost: [Int]) -> Int {
        let n = cost.count
        var dp = Array(repeating: 0, count: n)

        dp[0] = cost[0]
        dp[1] = cost[1]

        for i in 2..<n {
            dp[i] = cost[i] + min(dp[i - 1], dp[i - 2])
        }

        return min(dp[n - 1], dp[n - 2])
    }
}
```


### The End