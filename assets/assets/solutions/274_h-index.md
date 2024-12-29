# H-Index

## Problem Statement

Given an array of integers `citations` where `citations[i]` is the number of citations a researcher received for their `i-th` paper, compute the researcher's h-index.

The h-index is defined as the maximum value of `h` such that the researcher has published at least `h` papers that have each been cited at least `h` times.

## Input

```text
citations = [3, 0, 6, 1, 5]
```

## Output

```text
3
```

## Solutions

### Dart

```dart
int hIndex(List<int> citations) {
  citations.sort((a, b) => b - a);

  for (int i = 0; i < citations.length; i++) {
    if (citations[i] <= i) return i;
  }

  return citations.length;
}
```

### C#

```csharp
public class Solution {
    public int HIndex(int[] citations) {
        Array.Sort(citations, (a, b) => b.CompareTo(a));

        for (int i = 0; i < citations.Length; i++) {
            if (citations[i] <= i) return i;
        }

        return citations.Length;
    }
}
```

### Java

```java
class Solution {
    public int hIndex(int[] citations) {
        Arrays.sort(citations);
        int n = citations.length;

        for (int i = 0; i < n; i++) {
            if (citations[i] >= n - i) return n - i;
        }

        return 0;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun hIndex(citations: IntArray): Int {
        citations.sortDescending()
        
        for (i in citations.indices) {
            if (citations[i] <= i) return i
        }
        
        return citations.size
    }
}
```

### Swift

```swift
class Solution {
    func hIndex(_ citations: [Int]) -> Int {
        let sortedCitations = citations.sorted(by: >)

        for i in 0..<sortedCitations.count {
            if sortedCitations[i] <= i {
                return i
            }
        }

        return sortedCitations.count
    }
}
```

### The End

