# Best Time to Buy and Sell Stock with Cooldown

## Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the \(i^{th}\) day. Find the maximum profit you can achieve. You may complete as many transactions as you like (buy one and sell one share of the stock multiple times) with the following restrictions:

- After you sell your stock, you cannot buy stock on the next day (i.e., cooldown one day).
- You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

## Input

```text
prices = [1, 2, 3, 0, 2]
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int maxProfit(List<int> prices) {
  if (prices.length <= 1) return 0;

  final n = prices.length;
  final dp = List.generate(n, (_) => List<int>.filled(3, 0));

  dp[0][0] = 0; // No stock held on day 0
  dp[0][1] = -prices[0]; // Bought stock on day 0
  dp[0][2] = 0; // Cooldown on day 0

  for (int i = 1; i < n; i++) {
    dp[i][0] = max(dp[i - 1][0], dp[i - 1][2]); // No stock held on day i
    dp[i][1] = max(dp[i - 1][1], dp[i - 1][0] - prices[i]); // Bought stock on day i
    dp[i][2] = dp[i - 1][1] + prices[i]; // Sold stock on day i
  }

  return max(dp[n - 1][0], dp[n - 1][2]);
}
```

### C#

```csharp
public class Solution {
    public int MaxProfit(int[] prices) {
        if (prices.Length <= 1) return 0;

        int n = prices.Length;
        int[,] dp = new int[n, 3];

        dp[0, 0] = 0;         // No stock held on day 0
        dp[0, 1] = -prices[0]; // Bought stock on day 0
        dp[0, 2] = 0;         // Cooldown on day 0

        for (int i = 1; i < n; i++) {
            dp[i, 0] = Math.Max(dp[i - 1, 0], dp[i - 1, 2]);
            dp[i, 1] = Math.Max(dp[i - 1, 1], dp[i - 1, 0] - prices[i]);
            dp[i, 2] = dp[i - 1, 1] + prices[i];
        }

        return Math.Max(dp[n - 1, 0], dp[n - 1, 2]);
    }
}
```

### Java

```java
class Solution {
    public int maxProfit(int[] prices) {
        if (prices.length <= 1) return 0;

        int n = prices.length;
        int[][] dp = new int[n][3];

        dp[0][0] = 0; // No stock held on day 0
        dp[0][1] = -prices[0]; // Bought stock on day 0
        dp[0][2] = 0; // Cooldown on day 0

        for (int i = 1; i < n; i++) {
            dp[i][0] = Math.max(dp[i - 1][0], dp[i - 1][2]);
            dp[i][1] = Math.max(dp[i - 1][1], dp[i - 1][0] - prices[i]);
            dp[i][2] = dp[i - 1][1] + prices[i];
        }

        return Math.max(dp[n - 1][0], dp[n - 1][2]);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun maxProfit(prices: IntArray): Int {
        if (prices.size <= 1) return 0

        val n = prices.size
        val dp = Array(n) { IntArray(3) }

        dp[0][0] = 0
        dp[0][1] = -prices[0]
        dp[0][2] = 0

        for (i in 1 until n) {
            dp[i][0] = maxOf(dp[i - 1][0], dp[i - 1][2])
            dp[i][1] = maxOf(dp[i - 1][1], dp[i - 1][0] - prices[i])
            dp[i][2] = dp[i - 1][1] + prices[i]
        }

        return maxOf(dp[n - 1][0], dp[n - 1][2])
    }
}
```

### Swift

```swift
class Solution {
    func maxProfit(_ prices: [Int]) -> Int {
        if prices.count <= 1 { return 0 }

        let n = prices.count
        var dp = Array(repeating: Array(repeating: 0, count: 3), count: n)

        dp[0][0] = 0
        dp[0][1] = -prices[0]
        dp[0][2] = 0

        for i in 1..<n {
            dp[i][0] = max(dp[i - 1][0], dp[i - 1][2])
            dp[i][1] = max(dp[i - 1][1], dp[i - 1][0] - prices[i])
            dp[i][2] = dp[i - 1][1] + prices[i]
        }

        return max(dp[n - 1][0], dp[n - 1][2])
    }
}
```

### The End

