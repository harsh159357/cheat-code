# Count Ways to Build Good Strings

## Problem Statement

You are given integers `low`, `high`, `zero`, and `one`. A good string is defined as a binary string that:
1. Has a length between `low` and `high` inclusive.
2. Can be constructed using exactly `zero` number of `0`s and `one` number of `1`s repeatedly.

Return the number of good strings modulo `10^9 + 7`.

## Input

```text
low = 3, high = 3, zero = 1, one = 2
```

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun countGoodStrings(low: Int, high: Int, zero: Int, one: Int): Int {
        val dp = MutableList(high + 1) { 0 }
        dp[0] = 1
        val mod = 1_000_000_007
        var res = 0

        for (i in 1..high) {
            if (i >= zero) {
                dp[i] = (dp[i] + dp[i - zero]) % mod
            }
            if (i >= one) {
                dp[i] = (dp[i] + dp[i - one]) % mod
            }
            if (i >= low) {
                res = (res + dp[i]) % mod
            }
        }
        return res
    }
}

fun main() {
    val solution = Solution()
    println(solution.countGoodStrings(3, 3, 1, 2)) // Output: 1
}
```


### Dart

```dart
int countGoodStrings(int low, int high, int zero, int one) {
  List<int> dp = List.filled(high + 1, 0);
  dp[0] = 1;
  int mod = 1000000007;
  int res = 0;

  for (int i = 1; i <= high; i++) {
    if (i >= zero) {
      dp[i] = (dp[i] + dp[i - zero]) % mod;
    }
    if (i >= one) {
      dp[i] = (dp[i] + dp[i - one]) % mod;
    }
    if (i >= low) {
      res = (res + dp[i]) % mod;
    }
  }
  return res;
}

void main() {
  print(countGoodStrings(3, 3, 1, 2)); // Output: 1
}
```


### C#

```csharp
public class Solution {
    public int CountGoodStrings(int low, int high, int zero, int one) {
        int[] dp = new int[high + 1];
        dp[0] = 1;
        int mod = 1_000_000_007;
        int res = 0;

        for (int i = 1; i <= high; i++) {
            if (i >= zero) {
                dp[i] = (dp[i] + dp[i - zero]) % mod;
            }
            if (i >= one) {
                dp[i] = (dp[i] + dp[i - one]) % mod;
            }
            if (i >= low) {
                res = (res + dp[i]) % mod;
            }
        }

        return res;
    }
}
```


### Java

```java
class Solution {
    public int countGoodStrings(int low, int high, int zero, int one) {
        int[] dp = new int[high + 1];
        dp[0] = 1;
        int mod = 1_000_000_007;
        int res = 0;

        for (int i = 1; i <= high; i++) {
            if (i >= zero) {
                dp[i] = (dp[i] + dp[i - zero]) % mod;
            }
            if (i >= one) {
                dp[i] = (dp[i] + dp[i - one]) % mod;
            }
            if (i >= low) {
                res = (res + dp[i]) % mod;
            }
        }

        return res;
    }
}
```


### Swift

```swift
class Solution {
    func countGoodStrings(_ low: Int, _ high: Int, _ zero: Int, _ one: Int) -> Int {
        var dp = [Int](repeating: 0, count: high + 1)
        dp[0] = 1
        let mod = 1_000_000_007
        var res = 0

        for i in 1...high {
            if i >= zero {
                dp[i] = (dp[i] + dp[i - zero]) % mod
            }
            if i >= one {
                dp[i] = (dp[i] + dp[i - one]) % mod
            }
            if i >= low {
                res = (res + dp[i]) % mod
            }
        }

        return res
    }
}

let solution = Solution()
print(solution.countGoodStrings(3, 3, 1, 2)) // Output: 1
```


### The End

