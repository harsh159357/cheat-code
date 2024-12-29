# Find the Town Judge

## Problem Statement

In a town, there are `n` people labeled from `1` to `n`. A person `a` trusts a person `b` if `trust[i] = [a, b]`. If the town judge exists, the following conditions hold:

1. The town judge does not trust anyone.
2. Everybody (except the town judge) trusts the town judge.
3. There is exactly one person that satisfies these properties.

Return the label of the town judge if they exist, or `-1` otherwise.

## Input

```text
n = 4
trust = [[1, 3], [1, 4], [2, 3], [2, 4], [4, 3]]
```

## Output

```text
The town judge is: 3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun findJudge(n: Int, trust: Array<IntArray>): Int {
        val trustCount = IntArray(n + 1)

        for (pair in trust) {
            val person = pair[0]
            val trustedBy = pair[1]
            trustCount[person]-- // Person trusts someone
            trustCount[trustedBy]++ // Someone trusts person
        }

        for (i in 1..n) {
            if (trustCount[i] == n - 1) {
                return i
            }
        }

        return -1 // No judge found
    }
}
```

### Dart

```dart
int findJudge(int n, List<List<int>> trust) {
  List<int> trustCount = List.filled(n + 1, 0);

  for (List<int> pair in trust) {
    int person = pair[0];
    int trustedBy = pair[1];
    trustCount[person]--; // Person trusts someone
    trustCount[trustedBy]++; // Someone trusts person
  }

  for (int i = 1; i <= n; i++) {
    if (trustCount[i] == n - 1) {
      return i;
    }
  }

  return -1; // No judge found
}
```

### C#

```csharp
public class Solution {
    public int FindJudge(int n, int[][] trust) {
        int[] trustCount = new int[n + 1];

        foreach (var pair in trust) {
            trustCount[pair[0]]--; // Person trusts someone
            trustCount[pair[1]]++; // Someone trusts person
        }

        for (int i = 1; i <= n; i++) {
            if (trustCount[i] == n - 1) {
                return i;
            }
        }

        return -1; // No judge found
    }
}
```

### Java

```java
class Solution {
    public int findJudge(int n, int[][] trust) {
        int[] trustCount = new int[n + 1];

        for (int[] pair : trust) {
            trustCount[pair[0]]--; // Person trusts someone
            trustCount[pair[1]]++; // Someone trusts person
        }

        for (int i = 1; i <= n; i++) {
            if (trustCount[i] == n - 1) {
                return i;
            }
        }

        return -1; // No judge found
    }
}
```

### Swift

```swift
class Solution {
    func findJudge(_ n: Int, _ trust: [[Int]]) -> Int {
        var trustCount = [Int](repeating: 0, count: n + 1)

        for pair in trust {
            let person = pair[0]
            let trustedBy = pair[1]
            trustCount[person] -= 1 // Person trusts someone
            trustCount[trustedBy] += 1 // Someone trusts person
        }

        for i in 1...n {
            if trustCount[i] == n - 1 {
                return i
            }
        }

        return -1 // No judge found
    }
}
```

### The End