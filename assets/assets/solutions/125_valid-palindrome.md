# Valid Palindrome

## Problem Statement

Given a string `s`, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

---

###Input

```text
s = "A man, a plan, a canal: Panama"
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool isPalindrome(String s) {
  int left = 0;
  int right = s.length - 1;

  while (left < right) {
    while (left < right && !s[left].contains(RegExp(r'[a-zA-Z0-9]'))) {
      left++;
    }
    while (left < right && !s[right].contains(RegExp(r'[a-zA-Z0-9]'))) {
      right--;
    }
    if (s[left].toLowerCase() != s[right].toLowerCase()) {
      return false;
    }
    left++;
    right--;
  }
  return true;
}
```


### C#

```csharp
public class Solution {
    public bool IsPalindrome(string s) {
        int left = 0, right = s.Length - 1;

        while (left < right) {
            while (left < right && !char.IsLetterOrDigit(s[left])) {
                left++;
            }
            while (left < right && !char.IsLetterOrDigit(s[right])) {
                right--;
            }
            if (char.ToLower(s[left]) != char.ToLower(s[right])) {
                return false;
            }
            left++;
            right--;
        }

        return true;
    }
}
```


### Java

```java
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0, right = s.length() - 1;

        while (left < right) {
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }
            left++;
            right--;
        }

        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isPalindrome(s: String): Boolean {
        var left = 0
        var right = s.length - 1

        while (left < right) {
            while (left < right && !s[left].isLetterOrDigit()) {
                left++
            }
            while (left < right && !s[right].isLetterOrDigit()) {
                right--
            }
            if (s[left].toLowerCase() != s[right].toLowerCase()) {
                return false
            }
            left++
            right--
        }

        return true
    }
}
```


### Swift

```swift
class Solution {
    func isPalindrome(_ s: String) -> Bool {
        var left = s.startIndex
        var right = s.index(before: s.endIndex)

        while left < right {
            while left < right && !s[left].isLetter && !s[left].isNumber {
                left = s.index(after: left)
            }
            while left < right && !s[right].isLetter && !s[right].isNumber {
                right = s.index(before: right)
            }
            if s[left].lowercased() != s[right].lowercased() {
                return false
            }
            left = s.index(after: left)
            right = s.index(before: right)
        }
        return true
    }
}
```

### The End

