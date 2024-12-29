# Solving Questions With Brainpower

## Problem Statement

You are given a 2D integer array `questions` where `questions[i] = [points, brainpower]`.

The `points` is the number of points you earn if you solve the `i-th` question. The `brainpower` is the number of subsequent questions you must skip to solve the `i-th` question.

Return the maximum points you can earn while solving questions optimally.

## Input

```text
questions = [[3, 2], [4, 3], [4, 4], [2, 5]]
```

## Output

```text
5
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun mostPoints(questions: Array<IntArray>): Long {
        val dp = LongArray(questions.size + 1)

        for (i in (questions.size - 1) downTo 0) {
            val points = questions[i][0]
            val brainpower = questions[i][1]
            val take = if (i + brainpower + 1 >= dp.size) points.toLong() else points + dp[i + brainpower + 1]
            val notTake = dp[i + 1]
            dp[i] = maxOf(take, notTake)
        }

        return dp[0]
    }
}

fun main() {
    val questions = arrayOf(intArrayOf(3, 2), intArrayOf(4, 3), intArrayOf(4, 4), intArrayOf(2, 5))
    println(Solution().mostPoints(questions)) // Output: 5
}
```

### Dart

```dart
int mostPoints(List<List<int>> questions) {
  List<int> dp = List.filled(questions.length + 1, 0);

  for (int i = questions.length - 1; i >= 0; i--) {
    int points = questions[i][0];
    int brainpower = questions[i][1];
    int take = i + brainpower + 1 >= dp.length ? points : points + dp[i + brainpower + 1];
    int notTake = dp[i + 1];
    dp[i] = max(take, notTake);
  }

  return dp[0];
}

void main() {
  List<List<int>> questions = [
    [3, 2],
    [4, 3],
    [4, 4],
    [2, 5]
  ];
  print(mostPoints(questions)); // Output: 5
}
```

### C#

```csharp
public class Solution {
    public long MostPoints(int[][] questions) {
        long[] dp = new long[questions.Length + 1];

        for (int i = questions.Length - 1; i >= 0; i--) {
            int points = questions[i][0];
            int brainpower = questions[i][1];
            long take = i + brainpower + 1 >= dp.Length ? points : points + dp[i + brainpower + 1];
            long notTake = dp[i + 1];
            dp[i] = Math.Max(take, notTake);
        }

        return dp[0];
    }
}
```

### Java

```java
class Solution {
    public long mostPoints(int[][] questions) {
        long[] dp = new long[questions.length + 1];

        for (int i = questions.length - 1; i >= 0; i--) {
            int points = questions[i][0];
            int brainpower = questions[i][1];
            long take = i + brainpower + 1 >= dp.length ? points : points + dp[i + brainpower + 1];
            long notTake = dp[i + 1];
            dp[i] = Math.max(take, notTake);
        }

        return dp[0];
    }
}
```

### Swift

```swift
class Solution {
    func mostPoints(_ questions: [[Int]]) -> Int {
        var dp = [Int](repeating: 0, count: questions.count + 1)

        for i in stride(from: questions.count - 1, through: 0, by: -1) {
            let points = questions[i][0]
            let brainpower = questions[i][1]
            let take = i + brainpower + 1 >= dp.count ? points : points + dp[i + brainpower + 1]
            let notTake = dp[i + 1]
            dp[i] = max(take, notTake)
        }

        return dp[0]
    }
}

let questions = [[3, 2], [4, 3], [4, 4], [2, 5]]
print(Solution().mostPoints(questions)) // Output: 5
```

### The End