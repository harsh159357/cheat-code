# Is Subsequence

## Problem Statement

Given two strings `s` and `t`, return `true` if `s` is a subsequence of `t`, or `false` otherwise.

A subsequence of a string is a new string formed from the original string by deleting some (or none) of the characters without disturbing the relative positions of the remaining characters. For example, `"ace"` is a subsequence of `"abcde"`, but `"aec"` is not.

## Input

```text
s = "abc"
t = "ahbgdc"
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool isSubsequence(String s, String t) {
  int sIndex = 0, tIndex = 0;
  while (sIndex < s.length && tIndex < t.length) {
    if (s[sIndex] == t[tIndex]) {
      sIndex++;
    }
    tIndex++;
  }
  return sIndex == s.length;
}
```

### C#

```csharp
public class Solution {
    public bool IsSubsequence(string s, string t) {
        int sIndex = 0, tIndex = 0;
        while (sIndex < s.Length && tIndex < t.Length) {
            if (s[sIndex] == t[tIndex]) {
                sIndex++;
            }
            tIndex++;
        }
        return sIndex == s.Length;
    }
}
```

### Java

```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int sIndex = 0, tIndex = 0;
        while (sIndex < s.length() && tIndex < t.length()) {
            if (s.charAt(sIndex) == t.charAt(tIndex)) {
                sIndex++;
            }
            tIndex++;
        }
        return sIndex == s.length();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isSubsequence(s: String, t: String): Boolean {
        var sIndex = 0
        var tIndex = 0
        while (sIndex < s.length && tIndex < t.length) {
            if (s[sIndex] == t[tIndex]) {
                sIndex++
            }
            tIndex++
        }
        return sIndex == s.length
    }
}
```

### Swift

```swift
class Solution {
    func isSubsequence(_ s: String, _ t: String) -> Bool {
        var sIndex = 0
        var tIndex = 0
        let sArray = Array(s)
        let tArray = Array(t)
        
        while sIndex < sArray.count && tIndex < tArray.count {
            if sArray[sIndex] == tArray[tIndex] {
                sIndex += 1
            }
            tIndex += 1
        }
        return sIndex == sArray.count
    }
}
```

### The End