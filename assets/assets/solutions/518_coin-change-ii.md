# Coin Change II

## Problem Statement

You are given an integer `amount` and an array of integers `coins` representing the denominations of coins. Return the number of combinations that make up that amount. If no combination is possible, return `0`.

### Constraints

- Each coin can be used an unlimited number of times.
- The order of coins in combinations does not matter.

## Input

```text
amount = 5
coins = [1, 2, 5]
```

## Output

```text
4
```

## Solutions

### Dart

```dart
int change(int amount, List<int> coins) {
  List<int> dp = List.filled(amount + 1, 0);
  dp[0] = 1; // Base case: 1 way to make amount 0

  for (int coin in coins) {
    for (int i = coin; i <= amount; i++) {
      dp[i] += dp[i - coin];
    }
  }

  return dp[amount];
}

void main() {
  print("Number of combinations for amount 5: ${change(5, [1, 2, 5])}"); // Output: 4
  print("Number of combinations for amount 3: ${change(3, [2])}"); // Output: 0
}
```


### C#

```csharp
public class Solution {
    public int Change(int amount, int[] coins) {
        int[] dp = new int[amount + 1];
        dp[0] = 1; // Base case: 1 way to make amount 0

        foreach (int coin in coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] += dp[i - coin];
            }
        }

        return dp[amount]; // The result is stored at dp[amount]
    }
}
```


### Java

```java
class Solution {
    public int change(int amount, int[] coins) {
        int[] dp = new int[amount + 1];
        dp[0] = 1; // Base case: 1 way to make amount 0

        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] += dp[i - coin];
            }
        }

        return dp[amount]; // The result is stored at dp[amount]
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun change(amount: Int, coins: IntArray): Int {
        val dp = IntArray(amount + 1)
        dp[0] = 1 // Base case: 1 way to make amount 0

        for (coin in coins) {
            for (i in coin..amount) {
                dp[i] += dp[i - coin]
            }
        }

        return dp[amount]
    }
}

fun main() {
    val solution = Solution()
    println("Number of combinations for amount 5: ${solution.change(5, intArrayOf(1, 2, 5))}") // Output: 4
    println("Number of combinations for amount 3: ${solution.change(3, intArrayOf(2))}") // Output: 0
}
```


### Swift

```swift
class Solution {
    func change(_ amount: Int, _ coins: [Int]) -> Int {
        var dp = Array(repeating: 0, count: amount + 1)
        dp[0] = 1 // Base case: 1 way to make amount 0

        for coin in coins {
            for i in coin...amount {
                dp[i] += dp[i - coin]
            }
        }

        return dp[amount]
    }
}

// Example usage
let solution = Solution()
print(solution.change(5, [1, 2, 5])) // Output: 4
print(solution.change(3, [2])) // Output: 0
```

### The End