# Best Time to Buy and Sell Stock II

## Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the \(i^{th}\) day. On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it and sell it on the same day.

Return the maximum profit you can achieve.

---

## Input

```text
prices = [7, 1, 5, 3, 6, 4]
```

## Output

```text
7
```


## Solutions

### Dart

```dart
int maxProfit(List<int> prices) {
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
    public int MaxProfit(int[] prices) {
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
    public int maxProfit(int[] prices) {
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


### Kotlin

```kotlin
class Solution {
    fun maxProfit(prices: IntArray): Int {
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


### Swift

```swift
class Solution {
    func maxProfit(_ prices: [Int]) -> Int {
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

