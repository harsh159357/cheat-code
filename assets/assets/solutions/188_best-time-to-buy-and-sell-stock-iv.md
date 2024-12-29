# Best Time to Buy and Sell Stock IV

## Problem Statement

You are given an integer `k` and an array `prices` where `prices[i]` is the price of a stock on the `i`-th day. Design an algorithm to maximize your profit by executing at most `k` transactions.

**Note:** You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

---

## Input

```text
k = 2
prices = [3,2,6,5,0,3]
```

## Output

```text
7
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxProfit(k: Int, prices: IntArray): Int {
        if (prices.isEmpty()) return 0
        if (k >= prices.size / 2) return maxProfitWithInfiniteTransactions(prices)

        val dp = Array(k + 1) { IntArray(prices.size) }

        for (i in 1..k) {
            var maxDiff = -prices[0]
            for (j in 1 until prices.size) {
                dp[i][j] = maxOf(dp[i][j - 1], prices[j] + maxDiff)
                maxDiff = maxOf(maxDiff, dp[i - 1][j] - prices[j])
            }
        }
        return dp[k][prices.size - 1]
    }

    private fun maxProfitWithInfiniteTransactions(prices: IntArray): Int {
        var maxProfit = 0
        for (i in 1 until prices.size) {
            if (prices[i] > prices[i - 1]) {
                maxProfit += prices[i] - prices[i - 1]
            }
        }
        return maxProfit
    }
}
```

### Dart

```dart
int maxProfit(int k, List<int> prices) {
  if (prices.isEmpty) return 0;
  if (k >= prices.length ~/ 2) return maxProfitWithInfiniteTransactions(prices);

  List<List<int>> dp = List.generate(k + 1, (_) => List.filled(prices.length, 0));

  for (int i = 1; i <= k; i++) {
    int maxDiff = -prices[0];
    for (int j = 1; j < prices.length; j++) {
      dp[i][j] = max(dp[i][j - 1], prices[j] + maxDiff);
      maxDiff = max(maxDiff, dp[i - 1][j] - prices[j]);
    }
  }

  return dp[k][prices.length - 1];
}

int maxProfitWithInfiniteTransactions(List<int> prices) {
  int maxProfit = 0;
  for (int i = 1; i < prices.length; i++) {
    if (prices[i] > prices[i - 1]) {
      maxProfit += prices[i] - prices[i - 1];
    }
  }
  return maxProfit;
}
```

### C#

```csharp
public class Solution {
    public int MaxProfit(int k, int[] prices) {
        if (prices.Length == 0) return 0;
        if (k >= prices.Length / 2) return MaxProfitWithInfiniteTransactions(prices);

        int[,] dp = new int[k + 1, prices.Length];

        for (int i = 1; i <= k; i++) {
            int maxDiff = -prices[0];
            for (int j = 1; j < prices.Length; j++) {
                dp[i, j] = Math.Max(dp[i, j - 1], prices[j] + maxDiff);
                maxDiff = Math.Max(maxDiff, dp[i - 1, j] - prices[j]);
            }
        }
        return dp[k, prices.Length - 1];
    }

    private int MaxProfitWithInfiniteTransactions(int[] prices) {
        int maxProfit = 0;
        for (int i = 1; i < prices.Length; i++) {
            if (prices[i] > prices[i - 1]) {
                maxProfit += prices[i] - prices[i - 1];
            }
        }
        return maxProfit;
    }
}
```

### Java

```java
class Solution {
    public int maxProfit(int k, int[] prices) {
        if (prices.length == 0) return 0;
        if (k >= prices.length / 2) return maxProfitWithInfiniteTransactions(prices);

        int[][] dp = new int[k + 1][prices.length];

        for (int i = 1; i <= k; i++) {
            int maxDiff = -prices[0];
            for (int j = 1; j < prices.length; j++) {
                dp[i][j] = Math.max(dp[i][j - 1], prices[j] + maxDiff);
                maxDiff = Math.max(maxDiff, dp[i - 1][j] - prices[j]);
            }
        }
        return dp[k][prices.length - 1];
    }

    private int maxProfitWithInfiniteTransactions(int[] prices) {
        int maxProfit = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1]) {
                maxProfit += prices[i] - prices[i - 1];
            }
        }
        return maxProfit;
    }
}
```


### Swift

```swift
class Solution {
    func maxProfit(_ k: Int, _ prices: [Int]) -> Int {
        if prices.isEmpty { return 0 }
        if k >= prices.count / 2 { return maxProfitWithInfiniteTransactions(prices) }

        var dp = Array(repeating: Array(repeating: 0, count: prices.count), count: k + 1)

        for i in 1...k {
            var maxDiff = -prices[0]
            for j in 1..<prices.count {
                dp[i][j] = max(dp[i][j - 1], prices[j] + maxDiff)
                maxDiff = max(maxDiff, dp[i - 1][j] - prices[j])
            }
        }
        return dp[k][prices.count - 1]
    }

    private func maxProfitWithInfiniteTransactions(_ prices: [Int]) -> Int {
        var maxProfit = 0
        for i in 1..<prices.count {
            if prices[i] > prices[i - 1] {
                maxProfit += prices[i] - prices[i - 1]
            }
        }
        return maxProfit
    }
}
```

### The End

