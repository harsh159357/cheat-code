# Valid Anagram

## Problem Statement

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

## Input

```text
s = "anagram", t = "nagaram"
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool isAnagram(String s, String t) {
  if (s.length != t.length) return false;

  List<int> charCount = List.filled(26, 0);

  for (int i = 0; i < s.length; i++) {
    charCount[s.codeUnitAt(i) - 'a'.codeUnitAt(0)]++;
    charCount[t.codeUnitAt(i) - 'a'.codeUnitAt(0)]--;
  }

  for (int count in charCount) {
    if (count != 0) return false;
  }

  return true;
}
```

### C#

```csharp
public class Solution {
    public bool IsAnagram(string s, string t) {
        if (s.Length != t.Length) return false;

        int[] charCount = new int[26];

        foreach (char c in s) {
            charCount[c - 'a']++;
        }

        foreach (char c in t) {
            if (--charCount[c - 'a'] < 0) return false;
        }

        return true;
    }
}
```

### Java

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;

        int[] charCount = new int[26];

        for (char c : s.toCharArray()) {
            charCount[c - 'a']++;
        }

        for (char c : t.toCharArray()) {
            if (--charCount[c - 'a'] < 0) return false;
        }

        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isAnagram(s: String, t: String): Boolean {
        if (s.length != t.length) return false

        val charCount = IntArray(26)

        for (char in s) {
            charCount[char - 'a']++
        }

        for (char in t) {
            if (--charCount[char - 'a'] < 0) {
                return false
            }
        }

        return true
    }
}
```

### Swift

```swift
class Solution {
    func isAnagram(_ s: String, _ t: String) -> Bool {
        if s.count != t.count { return false }

        var charCount = [Int](repeating: 0, count: 26)

        for char in s {
            charCount[Int(char.asciiValue! - Character("a").asciiValue!)] += 1
        }

        for char in t {
            let index = Int(char.asciiValue! - Character("a").asciiValue!)
            charCount[index] -= 1
            if charCount[index] < 0 { return false }
        }

        return true
    }
}
```

### The End

