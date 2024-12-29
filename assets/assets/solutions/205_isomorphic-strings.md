# Isomorphic Strings

## Problem Statement

Given two strings `s` and `t`, determine if they are isomorphic.

Two strings are isomorphic if the characters in `s` can be replaced to get `t`.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

## Input

```text
s = "egg"
t = "add"
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool isIsomorphic(String s, String t) {
  Map<String, String> sToTMap = {};
  Map<String, String> tToSMap = {};

  for (int i = 0; i < s.length; i++) {
    String charS = s[i];
    String charT = t[i];

    if (sToTMap.containsKey(charS)) {
      if (sToTMap[charS] != charT) return false;
    } else {
      sToTMap[charS] = charT;
    }

    if (tToSMap.containsKey(charT)) {
      if (tToSMap[charT] != charS) return false;
    } else {
      tToSMap[charT] = charS;
    }
  }

  return true;
}
```

### C#

```csharp
public class Solution {
    public bool IsIsomorphic(string s, string t) {
        Dictionary<char, char> sToTMap = new Dictionary<char, char>();
        Dictionary<char, char> tToSMap = new Dictionary<char, char>();

        for (int i = 0; i < s.Length; i++) {
            char charS = s[i];
            char charT = t[i];

            if (sToTMap.ContainsKey(charS)) {
                if (sToTMap[charS] != charT) return false;
            } else {
                sToTMap[charS] = charT;
            }

            if (tToSMap.ContainsKey(charT)) {
                if (tToSMap[charT] != charS) return false;
            } else {
                tToSMap[charT] = charS;
            }
        }

        return true;
    }
}
```

### Java

```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        Map<Character, Character> sToTMap = new HashMap<>();
        Map<Character, Character> tToSMap = new HashMap<>();

        for (int i = 0; i < s.length(); i++) {
            char charS = s.charAt(i);
            char charT = t.charAt(i);

            if (sToTMap.containsKey(charS)) {
                if (sToTMap.get(charS) != charT) return false;
            } else {
                sToTMap.put(charS, charT);
            }

            if (tToSMap.containsKey(charT)) {
                if (tToSMap.get(charT) != charS) return false;
            } else {
                tToSMap.put(charT, charS);
            }
        }

        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isIsomorphic(s: String, t: String): Boolean {
        val sToTMap = mutableMapOf<Char, Char>()
        val tToSMap = mutableMapOf<Char, Char>()

        for (i in s.indices) {
            val charS = s[i]
            val charT = t[i]

            if (sToTMap.containsKey(charS)) {
                if (sToTMap[charS] != charT) return false
            } else {
                sToTMap[charS] = charT
            }

            if (tToSMap.containsKey(charT)) {
                if (tToSMap[charT] != charS) return false
            } else {
                tToSMap[charT] = charS
            }
        }

        return true
    }
}
```

### Swift

```swift
class Solution {
    func isIsomorphic(_ s: String, _ t: String) -> Bool {
        var sToTMap: [Character: Character] = [:]
        var tToSMap: [Character: Character] = [:]

        for (charS, charT) in zip(s, t) {
            if let mappedChar = sToTMap[charS] {
                if mappedChar != charT { return false }
            } else {
                sToTMap[charS] = charT
            }

            if let mappedChar = tToSMap[charT] {
                if mappedChar != charS { return false }
            } else {
                tToSMap[charT] = charS
            }
        }

        return true
    }
}
```

### The End

