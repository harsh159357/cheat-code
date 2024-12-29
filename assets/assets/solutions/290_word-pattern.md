# Word Pattern

## Problem Statement

Given a `pattern` and a string `s`, find if `s` follows the same pattern.

Here, follow means a bijection between a letter in `pattern` and a non-empty word in `s`.

## Input

```text
pattern = "abba"
s = "dog cat cat dog"
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool wordPattern(String pattern, String s) {
  List<String> words = s.split(" ");
  if (pattern.length != words.length) return false;

  Map<String, String> charToWord = {};
  Map<String, String> wordToChar = {};

  for (int i = 0; i < pattern.length; i++) {
    String char = pattern[i];
    String word = words[i];

    if (charToWord.containsKey(char)) {
      if (charToWord[char] != word) return false;
    } else {
      charToWord[char] = word;
    }

    if (wordToChar.containsKey(word)) {
      if (wordToChar[word] != char) return false;
    } else {
      wordToChar[word] = char;
    }
  }
  return true;
}
```

### C#

```csharp
public class Solution {
    public bool WordPattern(string pattern, string s) {
        string[] words = s.Split(' ');
        if (pattern.Length != words.Length) return false;

        Dictionary<char, string> charToWord = new();
        Dictionary<string, char> wordToChar = new();

        for (int i = 0; i < pattern.Length; i++) {
            char c = pattern[i];
            string word = words[i];

            if (charToWord.ContainsKey(c)) {
                if (charToWord[c] != word) return false;
            } else {
                charToWord[c] = word;
            }

            if (wordToChar.ContainsKey(word)) {
                if (wordToChar[word] != c) return false;
            } else {
                wordToChar[word] = c;
            }
        }
        return true;
    }
}
```

### Java

```java
class Solution {
    public boolean wordPattern(String pattern, String s) {
        String[] words = s.split(" ");
        if (pattern.length() != words.length) return false;

        Map<Character, String> charToWord = new HashMap<>();
        Map<String, Character> wordToChar = new HashMap<>();

        for (int i = 0; i < pattern.length(); i++) {
            char c = pattern.charAt(i);
            String word = words[i];

            if (charToWord.containsKey(c)) {
                if (!charToWord.get(c).equals(word)) return false;
            } else {
                charToWord.put(c, word);
            }

            if (wordToChar.containsKey(word)) {
                if (!wordToChar.get(word).equals(c)) return false;
            } else {
                wordToChar.put(word, c);
            }
        }
        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun wordPattern(pattern: String, s: String): Boolean {
        val words = s.split(" ")
        if (pattern.length != words.size) return false

        val charToWord = mutableMapOf<Char, String>()
        val wordToChar = mutableMapOf<String, Char>()

        for ((i, char) in pattern.withIndex()) {
            val word = words[i]

            if (charToWord.containsKey(char)) {
                if (charToWord[char] != word) return false
            } else {
                charToWord[char] = word
            }

            if (wordToChar.containsKey(word)) {
                if (wordToChar[word] != char) return false
            } else {
                wordToChar[word] = char
            }
        }
        return true
    }
}
```

### Swift

```swift
class Solution {
    func wordPattern(_ pattern: String, _ s: String) -> Bool {
        let words = s.split(separator: " ")
        if pattern.count != words.count { return false }

        var charToWord: [Character: String] = [:]
        var wordToChar: [String: Character] = [:]

        for (c, word) in zip(pattern, words) {
            let wordString = String(word)

            if let mappedWord = charToWord[c], mappedWord != wordString {
                return false
            }
            if let mappedChar = wordToChar[wordString], mappedChar != c {
                return false
            }

            charToWord[c] = wordString
            wordToChar[wordString] = c
        }

        return true
    }
}
```

### The End

