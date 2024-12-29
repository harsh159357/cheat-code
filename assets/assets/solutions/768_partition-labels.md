# Partition Labels

## Problem Statement

You are given a string `s`. You want to partition the string into as many parts as possible so that each letter appears in at most one part, and return a list of integers representing the size of these parts.

## Input

```text
s = "ababcbacadefegdehijhklij"
```

## Output

```text
[9, 7, 8]
```

## Solutions

### Dart

```dart
List<int> partitionLabels(String s) {
  List<int> lastIndices = List.filled(26, 0);
  for (int i = 0; i < s.length; i++) {
    lastIndices[s.codeUnitAt(i) - 'a'.codeUnitAt(0)] = i;
  }

  List<int> result = [];
  int start = 0, end = 0;

  for (int i = 0; i < s.length; i++) {
    end = end > lastIndices[s.codeUnitAt(i) - 'a'.codeUnitAt(0)] 
        ? end 
        : lastIndices[s.codeUnitAt(i) - 'a'.codeUnitAt(0)];
    if (i == end) {
      result.add(end - start + 1);
      start = end + 1;
    }
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public IList<int> PartitionLabels(string s) {
        int[] lastIndices = new int[26];
        for (int i = 0; i < s.Length; i++) {
            lastIndices[s[i] - 'a'] = i;
        }

        IList<int> result = new List<int>();
        int start = 0, end = 0;

        for (int i = 0; i < s.Length; i++) {
            end = Math.Max(end, lastIndices[s[i] - 'a']);
            if (i == end) {
                result.Add(end - start + 1);
                start = end + 1;
            }
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public List<Integer> partitionLabels(String s) {
        int[] lastIndices = new int[26];
        for (int i = 0; i < s.length(); i++) {
            lastIndices[s.charAt(i) - 'a'] = i;
        }

        List<Integer> result = new ArrayList<>();
        int start = 0, end = 0;

        for (int i = 0; i < s.length(); i++) {
            end = Math.max(end, lastIndices[s.charAt(i) - 'a']);
            if (i == end) {
                result.add(end - start + 1);
                start = end + 1;
            }
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun partitionLabels(s: String): List<Int> {
        val lastIndices = IntArray(26)
        for (i in s.indices) {
            lastIndices[s[i] - 'a'] = i
        }

        val result = mutableListOf<Int>()
        var start = 0
        var end = 0

        for (i in s.indices) {
            end = maxOf(end, lastIndices[s[i] - 'a'])
            if (i == end) {
                result.add(end - start + 1)
                start = end + 1
            }
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func partitionLabels(_ s: String) -> [Int] {
        var lastIndices = [Int](repeating: 0, count: 26)
        let asciiA = Character("a").asciiValue!

        for (i, char) in s.enumerated() {
            lastIndices[Int(char.asciiValue! - asciiA)] = i
        }

        var result = [Int]()
        var start = 0, end = 0

        for (i, char) in s.enumerated() {
            end = max(end, lastIndices[Int(char.asciiValue! - asciiA)])
            if i == end {
                result.append(end - start + 1)
                start = end + 1
            }
        }

        return result
    }
}
```

### The End