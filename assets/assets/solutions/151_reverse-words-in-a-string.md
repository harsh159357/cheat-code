# Reverse Words in a String

## Problem Statement

Given an input string `s`, reverse the order of the words. A word is defined as a sequence of non-space characters. The words in `s` will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

**Note:**
- Input string `s` may contain leading or trailing spaces. However, the returned string should not contain leading or trailing spaces.
- Reduce multiple spaces between two words to a single space in the returned string.

---

## Input

```text
s = "  hello world  "
```


## Output

```text
"world hello"
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun reverseWords(s: String): String {
        val words = mutableListOf<String>()
        var wordStart = -1
        
        for (i in s.indices) {
            if (s[i] != ' ' && (i == 0 || s[i - 1] == ' ')) {
                wordStart = i
            }
            if (s[i] != ' ' && (i == s.length - 1 || s[i + 1] == ' ')) {
                words.add(s.substring(wordStart, i + 1))
            }
        }
        
        return words.reversed().joinToString(" ")
    }
}
```


### Dart

```dart
String reverseWords(String s) {
  List<String> words = s.split(' ').where((word) => word.isNotEmpty).toList();
  return words.reversed.join(' ');
}
```


### C#

```csharp
public class Solution {
    public string ReverseWords(string s) {
        string[] words = s.Split(new char[] {' '}, StringSplitOptions.RemoveEmptyEntries);
        Array.Reverse(words);
        return string.Join(" ", words);
    }
}
```


### Java

```java
class Solution {
    public String reverseWords(String s) {
        String[] words = s.trim().split("\\s+");
        Collections.reverse(Arrays.asList(words));
        return String.join(" ", words);
    }
}
```


### Swift

```swift
class Solution {
    func reverseWords(_ s: String) -> String {
        let words = s.split(separator: " ").filter { !$0.isEmpty }
        return words.reversed().joined(separator: " ")
    }
}
```


### The End

