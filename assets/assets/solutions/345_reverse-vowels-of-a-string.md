# Reverse Vowels of a String

## Problem Statement

Given a string `s`, reverse only all the vowels in the string and return it.

The vowels are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`, both uppercase and lowercase.

## Input

```text
s = "hello"
```

## Output

```text
"holle"
```

---

## Solutions

### Dart

```dart
String reverseVowels(String s) {
  Set<String> vowels = {'a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'};
  List<String> chars = s.split('');
  int left = 0;
  int right = chars.length - 1;
  
  while (left < right) {
    if (vowels.contains(chars[left]) && vowels.contains(chars[right])) {
      String temp = chars[left];
      chars[left] = chars[right];
      chars[right] = temp;
      left++;
      right--;
    } else if (!vowels.contains(chars[left])) {
      left++;
    } else if (!vowels.contains(chars[right])) {
      right--;
    }
  }
  
  return chars.join();
}
```

### C#

```csharp
public class Solution {
    public string ReverseVowels(string s) {
        HashSet<char> vowels = new HashSet<char> {'a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'};
        char[] sChars = s.ToCharArray();
        int left = 0, right = s.Length - 1;

        while (left < right) {
            if (vowels.Contains(sChars[left]) && vowels.Contains(sChars[right])) {
                char temp = sChars[left];
                sChars[left] = sChars[right];
                sChars[right] = temp;
                left++;
                right--;
            } else if (!vowels.Contains(sChars[left])) {
                left++;
            } else if (!vowels.Contains(sChars[right])) {
                right--;
            }
        }

        return new string(sChars);
    }
}
```

### Java

```java
class Solution {
    public String reverseVowels(String s) {
        Set<Character> vowels = new HashSet<>(Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));
        char[] sChars = s.toCharArray();
        int left = 0, right = s.length() - 1;

        while (left < right) {
            if (vowels.contains(sChars[left]) && vowels.contains(sChars[right])) {
                char temp = sChars[left];
                sChars[left] = sChars[right];
                sChars[right] = temp;
                left++;
                right--;
            } else if (!vowels.contains(sChars[left])) {
                left++;
            } else if (!vowels.contains(sChars[right])) {
                right--;
            }
        }

        return new String(sChars);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun reverseVowels(s: String): String {
        val vowels = setOf('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U')
        val sChars = s.toCharArray()
        var left = 0
        var right = s.length - 1

        while (left < right) {
            if (sChars[left] in vowels && sChars[right] in vowels) {
                sChars[left] = sChars[right].also { sChars[right] = sChars[left] }
                left++
                right--
            } else if (sChars[left] !in vowels) {
                left++
            } else if (sChars[right] !in vowels) {
                right--
            }
        }

        return String(sChars)
    }
}
```

### Swift

```swift
class Solution {
    func reverseVowels(_ s: String) -> String {
        let vowels: Set<Character> = ["a", "e", "i", "o", "u", "A", "E", "I", "O", "U"]
        var sChars = Array(s)
        var left = 0
        var right = sChars.count - 1

        while left < right {
            if vowels.contains(sChars[left]) && vowels.contains(sChars[right]) {
                sChars.swapAt(left, right)
                left += 1
                right -= 1
            } else if !vowels.contains(sChars[left]) {
                left += 1
            } else if !vowels.contains(sChars[right]) {
                right -= 1
            }
        }

        return String(sChars)
    }
}
```

### The End

