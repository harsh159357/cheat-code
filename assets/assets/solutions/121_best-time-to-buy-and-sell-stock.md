# Best Time to Buy and Sell Stock

## Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the \( i^{th} \) day. You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`.

---

## Input

```text
prices = [7, 1, 5, 3, 6, 4]
```

## Output

```text
5
```

## Solutions

### Dart

```dart
int maxProfit(List<int> prices) {
  int minPrice = double.infinity.toInt();
  int maxProfit = 0;

  for (int price in prices) {
    minPrice = price < minPrice ? price : minPrice;
    maxProfit = (price - minPrice) > maxProfit ? (price - minPrice) : maxProfit;
  }

  return maxProfit;
}
```


### C#

```csharp
public class Solution {
    public int MaxProfit(int[] prices) {
        int minPrice = int.MaxValue;
        int maxProfit = 0;

        foreach (int price in prices) {
            if (price < minPrice) {
                minPrice = price;
            } else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice;
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
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;

        for (int price : prices) {
            if (price < minPrice) {
                minPrice = price;
            } else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice;
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
        var minPrice = Int.MAX_VALUE
        var maxProfit = 0

        for (price in prices) {
            minPrice = minOf(minPrice, price)
            maxProfit = maxOf(maxProfit, price - minPrice)
        }

        return maxProfit
    }
}
```


### Swift

```swift
class Solution {
    func maxProfit(_ prices: [Int]) -> Int {
        var minPrice = Int.max
        var maxProfit = 0

        for price in prices {
            minPrice = min(minPrice, price)
            maxProfit = max(maxProfit, price - minPrice)
        }

        return maxProfit
    }
}
```


### The End

