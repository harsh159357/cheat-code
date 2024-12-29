# Longest Arithmetic Subsequence

## Problem Statement

Given an array `A` of integers, return the length of the longest arithmetic subsequence in `A`.

An arithmetic subsequence of an array is a subsequence with a constant difference between consecutive terms.

## Input

```text
A = [3, 6, 9, 12]
```

## Output

```text
Length of the longest arithmetic subsequence: 4
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun longestArithSeqLength(A: IntArray): Int {
        val dp = Array(A.size) { HashMap<Int, Int>() }
        var maxLen = 0

        for (i in A.indices) {
            for (j in 0 until i) {
                val diff = A[i] - A[j]
                val prevLen = dp[j].getOrDefault(diff, 1)
                dp[i][diff] = prevLen + 1
                maxLen = maxOf(maxLen, dp[i][diff]!!)
            }
        }

        return maxLen
    }
}

fun main() {
    val solution = Solution()
    val A = intArrayOf(3, 6, 9, 12)
    println("Length of the longest arithmetic subsequence: ${solution.longestArithSeqLength(A)}")
}
```

### Dart

```dart
int longestArithSeqLength(List<int> A) {
  List<Map<int, int>> dp = List.generate(A.length, (_) => {});
  int maxLen = 0;

  for (int i = 0; i < A.length; i++) {
    for (int j = 0; j < i; j++) {
      int diff = A[i] - A[j];
      int prevLen = dp[j][diff] ?? 1;
      dp[i][diff] = prevLen + 1;
      maxLen = maxLen > dp[i][diff]! ? maxLen : dp[i][diff]!;
    }
  }

  return maxLen;
}

void main() {
  List<int> A = [3, 6, 9, 12];
  print("Length of the longest arithmetic subsequence: ${longestArithSeqLength(A)}");
}
```

### C#

```csharp
public class Solution {
    public int LongestArithSeqLength(int[] A) {
        var dp = new Dictionary<int, int>[A.Length];
        for (int i = 0; i < A.Length; i++) dp[i] = new Dictionary<int, int>();

        int maxLen = 0;

        for (int i = 0; i < A.Length; i++) {
            for (int j = 0; j < i; j++) {
                int diff = A[i] - A[j];
                int prevLen = dp[j].ContainsKey(diff) ? dp[j][diff] : 1;
                dp[i][diff] = prevLen + 1;
                maxLen = Math.Max(maxLen, dp[i][diff]);
            }
        }

        return maxLen;
    }
}
```

### Java

```java
import java.util.HashMap;

class Solution {
    public int longestArithSeqLength(int[] A) {
        HashMap<Integer, Integer>[] dp = new HashMap[A.length];
        for (int i = 0; i < A.length; i++) dp[i] = new HashMap<>();

        int maxLen = 0;

        for (int i = 0; i < A.length; i++) {
            for (int j = 0; j < i; j++) {
                int diff = A[i] - A[j];
                int prevLen = dp[j].getOrDefault(diff, 1);
                dp[i].put(diff, prevLen + 1);
                maxLen = Math.max(maxLen, dp[i].get(diff));
            }
        }

        return maxLen;
    }
}
```

### Swift

```swift
class Solution {
    func longestArithSeqLength(_ A: [Int]) -> Int {
        var dp = Array(repeating: [Int: Int](), count: A.count)
        var maxLen = 0

        for i in 0..<A.count {
            for j in 0..<i {
                let diff = A[i] - A[j]
                let prevLen = dp[j][diff] ?? 1
                dp[i][diff] = prevLen + 1
                maxLen = max(maxLen, dp[i][diff]!)
            }
        }

        return maxLen
    }
}
```

### The End