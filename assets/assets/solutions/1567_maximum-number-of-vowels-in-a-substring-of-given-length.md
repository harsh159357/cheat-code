# Maximum Number of Vowels in a Substring of Given Length

## Problem Statement

Given a string `s` and an integer `k`, return the maximum number of vowel letters in any substring of `s` with length `k`.

Vowel letters are: `'a', 'e', 'i', 'o', 'u'`.

## Input

```text
s = "abciiidef", k = 3
```

## Output

```text
3
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxVowels(s: String, k: Int): Int {
        val vowels = setOf('a', 'e', 'i', 'o', 'u')
        var maxCount = 0
        var count = 0

        for (i in s.indices) {
            if (i >= k) {
                if (s[i - k] in vowels) count--
            }
            if (s[i] in vowels) count++
            if (i >= k - 1) maxCount = maxOf(maxCount, count)
        }

        return maxCount
    }
}
```

### Dart

```dart
int maxVowels(String s, int k) {
  Set<String> vowels = {'a', 'e', 'i', 'o', 'u'};
  int maxCount = 0;
  int count = 0;

  for (int i = 0; i < s.length; i++) {
    if (i >= k && vowels.contains(s[i - k])) count--;
    if (vowels.contains(s[i])) count++;
    if (i >= k - 1) maxCount = max(maxCount, count);
  }

  return maxCount;
}
```

### C#

```csharp
public class Solution {
    public int MaxVowels(string s, int k) {
        HashSet<char> vowels = new HashSet<char> { 'a', 'e', 'i', 'o', 'u' };
        int maxCount = 0, count = 0;

        for (int i = 0; i < s.Length; i++) {
            if (i >= k && vowels.Contains(s[i - k])) count--;
            if (vowels.Contains(s[i])) count++;
            if (i >= k - 1) maxCount = Math.Max(maxCount, count);
        }

        return maxCount;
    }
}
```

### Java

```java
class Solution {
    public int maxVowels(String s, int k) {
        Set<Character> vowels = Set.of('a', 'e', 'i', 'o', 'u');
        int maxCount = 0, count = 0;

        for (int i = 0; i < s.length(); i++) {
            if (i >= k && vowels.contains(s.charAt(i - k))) count--;
            if (vowels.contains(s.charAt(i))) count++;
            if (i >= k - 1) maxCount = Math.max(maxCount, count);
        }

        return maxCount;
    }
}
```

### Swift

```swift
class Solution {
    func maxVowels(_ s: String, _ k: Int) -> Int {
        let vowels: Set<Character> = ["a", "e", "i", "o", "u"]
        var maxCount = 0
        var count = 0
        let chars = Array(s)

        for i in 0..<chars.count {
            if i >= k, vowels.contains(chars[i - k]) { count -= 1 }
            if vowels.contains(chars[i]) { count += 1 }
            if i >= k - 1 { maxCount = max(maxCount, count) }
        }

        return maxCount
    }
}
```

### The End