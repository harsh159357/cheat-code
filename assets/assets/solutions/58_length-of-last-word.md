# Length of Last Word

## Problem Statement

Given a string `s` consisting of words and spaces, return the length of the last word in the string.

A word is a maximal substring consisting of non-space characters only.

## Input

```text
s = "Hello World"
```

## Output

```text
5  
(Explanation: The last word is "World" with length 5.)
```
## Input

```text
s = "   fly me   to   the moon  "
```

## Output

```text
4  
(Explanation: The last word is "moon" with length 4.)
```

## Solutions

### Dart

```dart
int lengthOfLastWord(String s) {
  int length = 0;
  int i = s.length - 1;

  // Skip trailing spaces
  while (i >= 0 && s[i] == ' ') {
    i--;
  }

  // Count the characters of the last word
  while (i >= 0 && s[i] != ' ') {
    length++;
    i--;
  }

  return length;
}

void main() {
  print(lengthOfLastWord("Hello World")); // Output: 5
  print(lengthOfLastWord("   fly me   to   the moon  ")); // Output: 4
  print(lengthOfLastWord("luffy is still joyboy")); // Output: 6
}
```

### C#

```csharp
public class Solution {
    public int LengthOfLastWord(string s) {
        int length = 0;
        int i = s.Length - 1;

        // Skip trailing spaces
        while (i >= 0 && s[i] == ' ') {
            i--;
        }

        // Count the characters of the last word
        while (i >= 0 && s[i] != ' ') {
            length++;
            i--;
        }

        return length;
    }
}
```

### Java

```java
class Solution {
    public int lengthOfLastWord(String s) {
        int length = 0;
        int i = s.length() - 1;

        // Skip trailing spaces
        while (i >= 0 && s.charAt(i) == ' ') {
            i--;
        }

        // Count the characters of the last word
        while (i >= 0 && s.charAt(i) != ' ') {
            length++;
            i--;
        }

        return length;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun lengthOfLastWord(s: String): Int {
        var length = 0
        var i = s.length - 1

        // Skip trailing spaces
        while (i >= 0 && s[i] == ' ') {
            i--
        }

        // Count the characters of the last word
        while (i >= 0 && s[i] != ' ') {
            length++
            i--
        }

        return length
    }
}
```

### Swift

```swift
class Solution {
    func lengthOfLastWord(_ s: String) -> Int {
        var length = 0
        var i = s.count - 1
        let chars = Array(s)

        // Skip trailing spaces
        while i >= 0 && chars[i] == " " {
            i -= 1
        }

        // Count the characters of the last word
        while i >= 0 && chars[i] != " " {
            length += 1
            i -= 1
        }

        return length
    }
}

let solution = Solution()
print(solution.lengthOfLastWord("Hello World")) // Output: 5
print(solution.lengthOfLastWord("   fly me   to   the moon  ")) // Output: 4
print(solution.lengthOfLastWord("luffy is still joyboy")) // Output: 6
```

### The End

