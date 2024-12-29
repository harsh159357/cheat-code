# Find the Index of the First Occurrence in a String

## Problem Statement

Given two strings `haystack` and `needle`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

## Input

```text
haystack = "sadbutsad", needle = "sad"
```

## Output

```text
0  
(Explanation: The first occurrence of "sad" starts at index 0.)
```

## Solutions

### Dart

```dart
int strStr(String haystack, String needle) {
  if (needle.isEmpty) return 0;
  if (needle.length > haystack.length) return -1;

  for (int i = 0; i <= haystack.length - needle.length; i++) {
    if (haystack.substring(i, i + needle.length) == needle) {
      return i;
    }
  }
  return -1;
}

void main() {
  print(strStr("sadbutsad", "sad")); // Output: 0
  print(strStr("leetcode", "leeto")); // Output: -1
}
```

### C#

```csharp
public class Solution {
    public int StrStr(string haystack, string needle) {
        if (needle.Length == 0) return 0;
        if (needle.Length > haystack.Length) return -1;

        for (int i = 0; i <= haystack.Length - needle.Length; i++) {
            if (haystack.Substring(i, needle.Length) == needle) {
                return i;
            }
        }

        return -1;
    }
}
```

### Java

```java
class Solution {
    public int strStr(String haystack, String needle) {
        if (needle.isEmpty()) return 0;
        if (needle.length() > haystack.length()) return -1;

        for (int i = 0; i <= haystack.length() - needle.length(); i++) {
            if (haystack.substring(i, i + needle.length()).equals(needle)) {
                return i;
            }
        }

        return -1;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun strStr(haystack: String, needle: String): Int {
        if (needle.isEmpty()) return 0
        if (needle.length > haystack.length) return -1

        for (i in 0..haystack.length - needle.length) {
            if (haystack.substring(i, i + needle.length) == needle) {
                return i
            }
        }
        return -1
    }
}

fun main() {
    val haystack1 = "sadbutsad"
    val needle1 = "sad"
    println(Solution().strStr(haystack1, needle1)) // Output: 0

    val haystack2 = "leetcode"
    val needle2 = "leeto"
    println(Solution().strStr(haystack2, needle2)) // Output: -1
}
```

### Swift

```swift
class Solution {
    func strStr(_ haystack: String, _ needle: String) -> Int {
        if needle.isEmpty { return 0 }
        if needle.count > haystack.count { return -1 }

        for i in 0...(haystack.count - needle.count) {
            let start = haystack.index(haystack.startIndex, offsetBy: i)
            let end = haystack.index(start, offsetBy: needle.count)
            if haystack[start..<end] == needle {
                return i
            }
        }

        return -1
    }
}

let solution = Solution()
print(solution.strStr("sadbutsad", "sad")) // Output: 0
print(solution.strStr("leetcode", "leeto")) // Output: -1
```

### The End

