# Coin Change

## Problem Statement

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money. Return the fewest number of coins that you need to make up that amount. If that amount cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an infinite number of each kind of coin.

## Input

```text
coins = [1, 2, 5], amount = 11
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int coinChange(List<int> coins, int amount) {
  List<int> dp = List.filled(amount + 1, amount + 1);
  dp[0] = 0;

  for (int i = 1; i <= amount; i++) {
    for (int coin in coins) {
      if (coin <= i) {
        dp[i] = dp[i].min(dp[i - coin] + 1);
      }
    }
  }

  return dp[amount] > amount ? -1 : dp[amount];
}
```

### C#

```csharp
public class Solution {
    public int CoinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Array.Fill(dp, amount + 1);
        dp[0] = 0;

        for (int i = 1; i <= amount; i++) {
            foreach (int coin in coins) {
                if (coin <= i) {
                    dp[i] = Math.Min(dp[i], dp[i - coin] + 1);
                }
            }
        }

        return dp[amount] > amount ? -1 : dp[amount];
    }
}
```

### Java

```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1);
        dp[0] = 0;

        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (coin <= i) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }

        return dp[amount] > amount ? -1 : dp[amount];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun coinChange(coins: IntArray, amount: Int): Int {
        val dp = IntArray(amount + 1) { amount + 1 }
        dp[0] = 0

        for (i in 1..amount) {
            for (coin in coins) {
                if (coin <= i) {
                    dp[i] = minOf(dp[i], dp[i - coin] + 1)
                }
            }
        }

        return if (dp[amount] > amount) -1 else dp[amount]
    }
}
```

### Swift

```swift
class Solution {
    func coinChange(_ coins: [Int], _ amount: Int) -> Int {
        var dp = Array(repeating: amount + 1, count: amount + 1)
        dp[0] = 0

        for i in 1...amount {
            for coin in coins {
                if coin <= i {
                    dp[i] = min(dp[i], dp[i - coin] + 1)
                }
            }
        }

        return dp[amount] > amount ? -1 : dp[amount]
    }
}
```
### The End

