# Best Time to Buy and Sell Stock with Transaction Fee

## Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the `i`th day, and an integer `fee` representing the transaction fee for each sale. Return the maximum profit you can achieve.

You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction. You may not engage in multiple transactions simultaneously (you must sell the stock before you buy again).

## Input

```text
prices = [1, 3, 2, 8, 4, 9], fee = 2
```

## Output

```text
8
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxProfit(prices: IntArray, fee: Int): Int {
        var cash = 0
        var hold = -prices[0]
        for (i in 1 until prices.size) {
            cash = maxOf(cash, hold + prices[i] - fee)
            hold = maxOf(hold, cash - prices[i])
        }
        return cash
    }
}

fun main() {
    val prices = intArrayOf(1, 3, 2, 8, 4, 9)
    val fee = 2
    val solution = Solution()
    println("Maximum profit: ${solution.maxProfit(prices, fee)}") // Output: 8
}
```

### Dart

```dart
int maxProfit(List<int> prices, int fee) {
  int cash = 0;
  int hold = -prices[0];

  for (int i = 1; i < prices.length; i++) {
    cash = (cash > hold + prices[i] - fee) ? cash : (hold + prices[i] - fee);
    hold = (hold > cash - prices[i]) ? hold : (cash - prices[i]);
  }

  return cash;
}

void main() {
  List<int> prices = [1, 3, 2, 8, 4, 9];
  int fee = 2;
  print("Maximum profit: ${maxProfit(prices, fee)}"); // Output: 8
}
```


### C#

```csharp
public class Solution {
    public int MaxProfit(int[] prices, int fee) {
        int cash = 0, hold = -prices[0];

        for (int i = 1; i < prices.Length; i++) {
            cash = Math.Max(cash, hold + prices[i] - fee);
            hold = Math.Max(hold, cash - prices[i]);
        }

        return cash;
    }
}
```


### Java

```java
class Solution {
    public int maxProfit(int[] prices, int fee) {
        int cash = 0;
        int hold = -prices[0];

        for (int i = 1; i < prices.length; i++) {
            cash = Math.max(cash, hold + prices[i] - fee);
            hold = Math.max(hold, cash - prices[i]);
        }

        return cash;
    }
}
```


### Swift

```swift
class Solution {
    func maxProfit(_ prices: [Int], _ fee: Int) -> Int {
        var cash = 0
        var hold = -prices[0]

        for i in 1..<prices.count {
            cash = max(cash, hold + prices[i] - fee)
            hold = max(hold, cash - prices[i])
        }

        return cash
    }
}

// Example usage
let prices = [1, 3, 2, 8, 4, 9]
let fee = 2
let solution = Solution()
print("Maximum profit: \(solution.maxProfit(prices, fee))") // Output: 8
```

### The End