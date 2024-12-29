# Ransom Note

## Problem Statement

Given two strings `ransomNote` and `magazine`, return `true` if `ransomNote` can be constructed from the characters in `magazine` and `false` otherwise.

Each character in `magazine` can only be used once in `ransomNote`.

## Input

```text
ransomNote = "aa", magazine = "aab"
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool canConstruct(String ransomNote, String magazine) {
  final charFrequency = <String, int>{};

  // Populate the map with characters from magazine and their frequencies
  for (var char in magazine.split('')) {
    charFrequency[char] = (charFrequency[char] ?? 0) + 1;
  }

  // Decrement the frequency of characters from ransomNote in the map
  for (var char in ransomNote.split('')) {
    if (!charFrequency.containsKey(char) || charFrequency[char]! == 0) {
      return false;
    }
    charFrequency[char] = charFrequency[char]! - 1;
  }

  return true;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public bool CanConstruct(string ransomNote, string magazine) {
        var charFrequency = new Dictionary<char, int>();

        foreach (var c in magazine) {
            if (!charFrequency.ContainsKey(c)) {
                charFrequency[c] = 0;
            }
            charFrequency[c]++;
        }

        foreach (var c in ransomNote) {
            if (!charFrequency.ContainsKey(c) || charFrequency[c] == 0) {
                return false;
            }
            charFrequency[c]--;
        }

        return true;
    }
}
```

### Java

```java
import java.util.HashMap;

class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        HashMap<Character, Integer> charFrequency = new HashMap<>();

        for (char c : magazine.toCharArray()) {
            charFrequency.put(c, charFrequency.getOrDefault(c, 0) + 1);
        }

        for (char c : ransomNote.toCharArray()) {
            if (!charFrequency.containsKey(c) || charFrequency.get(c) == 0) {
                return false;
            }
            charFrequency.put(c, charFrequency.get(c) - 1);
        }

        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun canConstruct(ransomNote: String, magazine: String): Boolean {
        val charFrequency = mutableMapOf<Char, Int>()

        for (char in magazine) {
            charFrequency[char] = charFrequency.getOrDefault(char, 0) + 1
        }

        for (char in ransomNote) {
            if (!charFrequency.containsKey(char) || charFrequency[char] == 0) {
                return false
            }
            charFrequency[char] = charFrequency[char]!! - 1
        }

        return true
    }
}
```

### Swift

```swift
class Solution {
    func canConstruct(_ ransomNote: String, _ magazine: String) -> Bool {
        var charFrequency = [Character: Int]()

        for char in magazine {
            charFrequency[char, default: 0] += 1
        }

        for char in ransomNote {
            if let count = charFrequency[char], count > 0 {
                charFrequency[char]! -= 1
            } else {
                return false
            }
        }

        return true
    }
}
```

### The End