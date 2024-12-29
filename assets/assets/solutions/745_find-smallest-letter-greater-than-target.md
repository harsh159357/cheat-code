# Find Smallest Letter Greater Than Target

## Problem Statement

Given a list of sorted characters `letters` and a target character `target`, return the smallest character in the list that is strictly greater than `target`. If no such character exists, return the first character in the list.

## Input

```text
letters = ['c', 'f', 'j']
target = 'a'
```

## Output

```text
c
```

## Solutions

### Dart

```dart
String nextGreatestLetter(List<String> letters, String target) {
  int left = 0, right = letters.length;

  while (left < right) {
    int mid = left + (right - left) ~/ 2;

    if (letters[mid].compareTo(target) <= 0) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }

  return left == letters.length ? letters[0] : letters[left];
}
```

### C#

```csharp
public class Solution {
    public char NextGreatestLetter(char[] letters, char target) {
        int left = 0, right = letters.Length;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (letters[mid] <= target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return left == letters.Length ? letters[0] : letters[left];
    }
}
```

### Java

```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int left = 0, right = letters.length;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (letters[mid] <= target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        return left == letters.length ? letters[0] : letters[left];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun nextGreatestLetter(letters: CharArray, target: Char): Char {
        var left = 0
        var right = letters.size

        while (left < right) {
            val mid = left + (right - left) / 2

            if (letters[mid] <= target) {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return if (left == letters.size) letters[0] else letters[left]
    }
}
```

### Swift

```swift
class Solution {
    func nextGreatestLetter(_ letters: [Character], _ target: Character) -> Character {
        var left = 0
        var right = letters.count

        while left < right {
            let mid = left + (right - left) / 2

            if letters[mid] <= target {
                left = mid + 1
            } else {
                right = mid
            }
        }

        return left == letters.count ? letters[0] : letters[left]
    }
}
```


### The End