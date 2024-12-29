# Triangle

## Problem Statement

Given a triangle array, return the minimum path sum from top to bottom. Each step, you may move to an adjacent number of the row below.

## Input

```text
triangle = [[2],
            [3,4],
           [6,5,7],
          [4,1,8,3]]
```

## Output

```text
11
```

## Solutions

### Dart

```dart
int minimumTotal(List<List<int>> triangle) {
  int n = triangle.length;
  List<int> dp = List.from(triangle[n - 1]);

  for (int i = n - 2; i >= 0; i--) {
    for (int j = 0; j <= i; j++) {
      dp[j] = triangle[i][j] + min(dp[j], dp[j + 1]);
    }
  }

  return dp[0];
}
```

---

### C#

```csharp
public class Solution {
    public int MinimumTotal(IList<IList<int>> triangle) {
        int n = triangle.Count;
        int[] dp = new int[n];
        for (int i = 0; i < n; i++) {
            dp[i] = triangle[n - 1][i];
        }

        for (int i = n - 2; i >= 0; i--) {
            for (int j = 0; j <= i; j++) {
                dp[j] = triangle[i][j] + Math.Min(dp[j], dp[j + 1]);
            }
        }

        return dp[0];
    }
}
```

---

### Java

```java
class Solution {
    public int minimumTotal(List<List<Integer>> triangle) {
        int n = triangle.size();
        int[] dp = new int[n];
        for (int i = 0; i < n; i++) {
            dp[i] = triangle.get(n - 1).get(i);
        }

        for (int i = n - 2; i >= 0; i--) {
            for (int j = 0; j <= i; j++) {
                dp[j] = triangle.get(i).get(j) + Math.min(dp[j], dp[j + 1]);
            }
        }

        return dp[0];
    }
}
```

---

### Kotlin

```kotlin
class Solution {
    fun minimumTotal(triangle: List<List<Int>>): Int {
        val n = triangle.size
        val dp = IntArray(n) { triangle[n - 1][it] }
        for (i in n - 2 downTo 0) {
            for (j in 0..i) {
                dp[j] = minOf(dp[j], dp[j + 1]) + triangle[i][j]
            }
        }
        return dp[0]
    }
}
```

---

### Swift

```swift
class Solution {
    func minimumTotal(_ triangle: [[Int]]) -> Int {
        let n = triangle.count
        var dp = triangle[n - 1]

        for i in (0..<(n - 1)).reversed() {
            for j in 0...i {
                dp[j] = triangle[i][j] + min(dp[j], dp[j + 1])
            }
        }

        return dp[0]
    }
}
```


### The End

