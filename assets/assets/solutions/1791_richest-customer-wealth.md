# Richest Customer Wealth

## Problem Statement

You are given an `m x n` integer grid `accounts` where `accounts[i][j]` is the amount of money the `i-th` customer has in the `j-th` bank. Return the **wealth** that the richest customer has.

A customer's wealth is the sum of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.

## Input

```text
accounts = [[1,2,3],[3,2,1]]
```

## Output

```text
6
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun maximumWealth(accounts: Array<IntArray>): Int {
        var maxWealth = 0
        for (customerWealth in accounts) {
            val wealth = customerWealth.sum()
            maxWealth = maxOf(maxWealth, wealth)
        }
        return maxWealth
    }
}

fun main() {
    val accounts = arrayOf(
        intArrayOf(1, 2, 3),
        intArrayOf(3, 2, 1)
    )
    println(Solution().maximumWealth(accounts)) // Output: 6
}
```

### Dart

```dart
int maximumWealth(List<List<int>> accounts) {
  int maxWealth = 0;
  for (var customerWealth in accounts) {
    int wealth = customerWealth.reduce((a, b) => a + b);
    maxWealth = max(maxWealth, wealth);
  }
  return maxWealth;
}

void main() {
  List<List<int>> accounts = [
    [1, 2, 3],
    [3, 2, 1]
  ];
  print(maximumWealth(accounts)); // Output: 6
}
```

### C#

```csharp
public class Solution {
    public int MaximumWealth(int[][] accounts) {
        int maxWealth = 0;
        foreach (var customerWealth in accounts) {
            int wealth = customerWealth.Sum();
            maxWealth = Math.Max(maxWealth, wealth);
        }
        return maxWealth;
    }
}
```

### Java

```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int maxWealth = 0;
        for (int[] customerWealth : accounts) {
            int wealth = 0;
            for (int money : customerWealth) {
                wealth += money;
            }
            maxWealth = Math.max(maxWealth, wealth);
        }
        return maxWealth;
    }
}
```

### Swift

```swift
class Solution {
    func maximumWealth(_ accounts: [[Int]]) -> Int {
        var maxWealth = 0
        for customerWealth in accounts {
            let wealth = customerWealth.reduce(0, +)
            maxWealth = max(maxWealth, wealth)
        }
        return maxWealth
    }
}

let accounts = [[1, 2, 3], [3, 2, 1]]
print(Solution().maximumWealth(accounts)) // Output: 6
```

### The End