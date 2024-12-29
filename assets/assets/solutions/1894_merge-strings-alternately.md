# Merge Strings Alternately

## Problem Statement

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

## Input

```text
word1 = "abc", word2 = "pqr"
```

## Output

```text
"apbqcr"
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun mergeAlternately(word1: String, word2: String): String {
        val merged = StringBuilder()
        val minLen = minOf(word1.length, word2.length)
        for (i in 0 until minLen) {
            merged.append(word1[i]).append(word2[i])
        }
        if (word1.length > minLen) merged.append(word1.substring(minLen))
        if (word2.length > minLen) merged.append(word2.substring(minLen))
        return merged.toString()
    }
}

fun main() {
    val word1 = "abc"
    val word2 = "pqr"
    println(Solution().mergeAlternately(word1, word2)) // Output: "apbqcr"
}
```

### Dart

```dart
String mergeAlternately(String word1, String word2) {
  StringBuffer merged = StringBuffer();
  int minLen = word1.length < word2.length ? word1.length : word2.length;

  for (int i = 0; i < minLen; i++) {
    merged.write(word1[i]);
    merged.write(word2[i]);
  }

  if (word1.length > minLen) {
    merged.write(word1.substring(minLen));
  }
  if (word2.length > minLen) {
    merged.write(word2.substring(minLen));
  }

  return merged.toString();
}

void main() {
  print(mergeAlternately("abc", "pqr")); // Output: "apbqcr"
}
```

### C#

```csharp
public class Solution {
    public string MergeAlternately(string word1, string word2) {
        var merged = new StringBuilder();
        int minLen = Math.Min(word1.Length, word2.Length);

        for (int i = 0; i < minLen; i++) {
            merged.Append(word1[i]);
            merged.Append(word2[i]);
        }

        if (word1.Length > minLen) {
            merged.Append(word1.Substring(minLen));
        }
        if (word2.Length > minLen) {
            merged.Append(word2.Substring(minLen));
        }

        return merged.ToString();
    }
}
```

### Java

```java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        StringBuilder merged = new StringBuilder();
        int minLen = Math.min(word1.length(), word2.length());

        for (int i = 0; i < minLen; i++) {
            merged.append(word1.charAt(i)).append(word2.charAt(i));
        }

        if (word1.length() > minLen) {
            merged.append(word1.substring(minLen));
        }
        if (word2.length() > minLen) {
            merged.append(word2.substring(minLen));
        }

        return merged.toString();
    }
}
```

### Swift

```swift
class Solution {
    func mergeAlternately(_ word1: String, _ word2: String) -> String {
        var merged = ""
        let word1Array = Array(word1)
        let word2Array = Array(word2)
        let minLen = min(word1Array.count, word2Array.count)

        for i in 0..<minLen {
            merged.append(word1Array[i])
            merged.append(word2Array[i])
        }

        if word1Array.count > minLen {
            merged.append(contentsOf: word1Array[minLen...])
        }
        if word2Array.count > minLen {
            merged.append(contentsOf: word2Array[minLen...])
        }

        return merged
    }
}

let word1 = "abc"
let word2 = "pqr"
print(Solution().mergeAlternately(word1, word2)) // Output: "apbqcr"
```

### The End