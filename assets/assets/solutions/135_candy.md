# Candy Distribution

## Problem Statement

There are `n` children standing in a line. Each child is assigned a rating value given in the integer array `ratings`.

You are giving candies to these children subjected to the following requirements:

1. Each child must have at least one candy.
2. Children with a higher rating get more candies than their neighbors.

Return the minimum number of candies you need to have to distribute the candies to the children.

---

## Input

```text
ratings = [1, 0, 2]
```

## Output

```text
5
```

## Solutions

### Dart

```dart
int candy(List<int> ratings) {
  int n = ratings.length;
  List<int> candies = List.filled(n, 1);

  for (int i = 1; i < n; i++) {
    if (ratings[i] > ratings[i - 1]) {
      candies[i] = candies[i - 1] + 1;
    }
  }

  for (int i = n - 2; i >= 0; i--) {
    if (ratings[i] > ratings[i + 1]) {
      candies[i] = max(candies[i], candies[i + 1] + 1);
    }
  }

  return candies.reduce((a, b) => a + b);
}
```

### C#

```csharp
public class Solution {
    public int Candy(int[] ratings) {
        int n = ratings.Length;
        int[] candies = new int[n];
        Array.Fill(candies, 1);

        for (int i = 1; i < n; i++) {
            if (ratings[i] > ratings[i - 1]) {
                candies[i] = candies[i - 1] + 1;
            }
        }

        for (int i = n - 2; i >= 0; i--) {
            if (ratings[i] > ratings[i + 1]) {
                candies[i] = Math.Max(candies[i], candies[i + 1] + 1);
            }
        }

        return candies.Sum();
    }
}
```


### Java

```java
class Solution {
    public int candy(int[] ratings) {
        int n = ratings.length;
        int[] candies = new int[n];
        Arrays.fill(candies, 1);

        for (int i = 1; i < n; i++) {
            if (ratings[i] > ratings[i - 1]) {
                candies[i] = candies[i - 1] + 1;
            }
        }

        for (int i = n - 2; i >= 0; i--) {
            if (ratings[i] > ratings[i + 1]) {
                candies[i] = Math.max(candies[i], candies[i + 1] + 1);
            }
        }

        int totalCandies = 0;
        for (int candy : candies) {
            totalCandies += candy;
        }
        return totalCandies;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun candy(ratings: IntArray): Int {
        val n = ratings.size
        val candies = IntArray(n) { 1 }

        for (i in 1 until n) {
            if (ratings[i] > ratings[i - 1]) {
                candies[i] = candies[i - 1] + 1
            }
        }

        for (i in n - 2 downTo 0) {
            if (ratings[i] > ratings[i + 1]) {
                candies[i] = maxOf(candies[i], candies[i + 1] + 1)
            }
        }

        return candies.sum()
    }
}
```


### Swift

```swift
class Solution {
    func candy(_ ratings: [Int]) -> Int {
        let n = ratings.count
        var candies = Array(repeating: 1, count: n)

        for i in 1..<n {
            if ratings[i] > ratings[i - 1] {
                candies[i] = candies[i - 1] + 1
            }
        }

        for i in stride(from: n - 2, through: 0, by: -1) {
            if ratings[i] > ratings[i + 1] {
                candies[i] = max(candies[i], candies[i + 1] + 1)
            }
        }

        return candies.reduce(0, +)
    }
}
```

### The End

