# Minimum Cost for Tickets

## Problem Statement

You have a set of days that you will travel, and a set of costs for 1-day, 7-day, and 30-day passes. Each pass allows unlimited travel for the respective duration starting on the day of purchase. Return the minimum cost to travel for all the given days.

## Input

```text
days = [1, 4, 6, 7, 8, 20]
costs = [2, 7, 15]
```

## Output

```text
11
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun mincostTickets(days: IntArray, costs: IntArray): Int {
        val dp = IntArray(days.size + 1)
        
        for (i in 1 until dp.size) {
            dp[i] = dp[i - 1] + costs[0]
            
            var j = i - 1
            while (j >= 0 && days[i - 1] - days[j] < 7) {
                dp[i] = minOf(dp[i], dp[j] + costs[1])
                j--
            }
            
            j = i - 1
            while (j >= 0 && days[i - 1] - days[j] < 30) {
                dp[i] = minOf(dp[i], dp[j] + costs[2])
                j--
            }
        }
        return dp[dp.size - 1]
    }
}
```

### Dart

```dart
int mincostTickets(List<int> days, List<int> costs) {
  List<int> dp = List.filled(days.length + 1, 0);

  for (int i = 1; i < dp.length; i++) {
    dp[i] = dp[i - 1] + costs[0];

    int j = i - 1;
    while (j >= 0 && days[i - 1] - days[j] < 7) {
      dp[i] = (dp[i] < dp[j] + costs[1]) ? dp[i] : dp[j] + costs[1];
      j--;
    }

    j = i - 1;
    while (j >= 0 && days[i - 1] - days[j] < 30) {
      dp[i] = (dp[i] < dp[j] + costs[2]) ? dp[i] : dp[j] + costs[2];
      j--;
    }
  }

  return dp.last;
}
```

### C#

```csharp
public class Solution {
    public int MincostTickets(int[] days, int[] costs) {
        int[] dp = new int[days.Length + 1];

        for (int i = 1; i < dp.Length; i++) {
            dp[i] = dp[i - 1] + costs[0];

            int j = i - 1;
            while (j >= 0 && days[i - 1] - days[j] < 7) {
                dp[i] = Math.Min(dp[i], dp[j] + costs[1]);
                j--;
            }

            j = i - 1;
            while (j >= 0 && days[i - 1] - days[j] < 30) {
                dp[i] = Math.Min(dp[i], dp[j] + costs[2]);
                j--;
            }
        }

        return dp[dp.Length - 1];
    }
}
```

### Java

```java
class Solution {
    public int mincostTickets(int[] days, int[] costs) {
        int[] dp = new int[days.length + 1];

        for (int i = 1; i < dp.length; i++) {
            dp[i] = dp[i - 1] + costs[0];

            int j = i - 1;
            while (j >= 0 && days[i - 1] - days[j] < 7) {
                dp[i] = Math.min(dp[i], dp[j] + costs[1]);
                j--;
            }

            j = i - 1;
            while (j >= 0 && days[i - 1] - days[j] < 30) {
                dp[i] = Math.min(dp[i], dp[j] + costs[2]);
                j--;
            }
        }

        return dp[dp.length - 1];
    }
}
```

### Swift

```swift
class Solution {
    func mincostTickets(_ days: [Int], _ costs: [Int]) -> Int {
        var dp = Array(repeating: 0, count: days.count + 1)

        for i in 1..<dp.count {
            dp[i] = dp[i - 1] + costs[0]

            var j = i - 1
            while j >= 0 && days[i - 1] - days[j] < 7 {
                dp[i] = min(dp[i], dp[j] + costs[1])
                j -= 1
            }

            j = i - 1
            while j >= 0 && days[i - 1] - days[j] < 30 {
                dp[i] = min(dp[i], dp[j] + costs[2])
                j -= 1
            }
        }

        return dp.last!
    }
}
```

### The End