# Best Time to Buy and Sell Stock III

## Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the \(i^{th}\) day.  
Find the maximum profit you can achieve. You may complete at most two transactions.

**Note**: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

---

## Input

```text
prices = [3,3,5,0,0,3,1,4]
```

## Output

```text
6
```

## Solutions

### Dart

```dart
int maxProfit(List<int> prices) {
  int f1 = -prices[0]; // First buy
  int f2 = 0;         // First sell
  int f3 = -prices[0]; // Second buy
  int f4 = 0;         // Second sell

  for (int p in prices) {
    f1 = max(f1, -p);
    f2 = max(f2, f1 + p);
    f3 = max(f3, f2 - p);
    f4 = max(f4, f3 + p);
  }

  return f4;
}
```


### C#

```csharp
public class Solution {
    public int MaxProfit(int[] prices) {
        int f1 = -prices[0];
        int f2 = 0;
        int f3 = -prices[0];
        int f4 = 0;

        foreach (int p in prices) {
            f1 = Math.Max(f1, -p);
            f2 = Math.Max(f2, f1 + p);
            f3 = Math.Max(f3, f2 - p);
            f4 = Math.Max(f4, f3 + p);
        }

        return f4;
    }
}
```


### Java

```java
class Solution {
    public int maxProfit(int[] prices) {
        int f1 = -prices[0];
        int f2 = 0;
        int f3 = -prices[0];
        int f4 = 0;

        for (int p : prices) {
            f1 = Math.max(f1, -p);
            f2 = Math.max(f2, f1 + p);
            f3 = Math.max(f3, f2 - p);
            f4 = Math.max(f4, f3 + p);
        }

        return f4;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun maxProfit(prices: IntArray): Int {
        var f1 = -prices[0] // First buy
        var f2 = 0          // First sell
        var f3 = -prices[0] // Second buy
        var f4 = 0          // Second sell

        for (p in prices) {
            f1 = maxOf(f1, -p)
            f2 = maxOf(f2, f1 + p)
            f3 = maxOf(f3, f2 - p)
            f4 = maxOf(f4, f3 + p)
        }

        return f4
    }
}
```


### Swift

```swift
class Solution {
    func maxProfit(_ prices: [Int]) -> Int {
        var f1 = -prices[0] // First buy
        var f2 = 0          // First sell
        var f3 = -prices[0] // Second buy
        var f4 = 0          // Second sell

        for p in prices {
            f1 = max(f1, -p)
            f2 = max(f2, f1 + p)
            f3 = max(f3, f2 - p)
            f4 = max(f4, f3 + p)
        }

        return f4
    }
}
```

### The End

