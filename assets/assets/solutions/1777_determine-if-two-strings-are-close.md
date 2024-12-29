# Determine if Two Strings Are Close

## Problem Statement

Two strings are considered **close** if you can transform one string into another using the following operations:
1. Swap any two existing characters.
2. Transform every occurrence of one existing character into another existing character and vice versa.

You are given two strings `word1` and `word2`. Return `true` if `word1` and `word2` are close, and `false` otherwise.

## Input

```text
word1 = "abc", word2 = "bca"
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun closeStrings(word1: String, word2: String): Boolean {
        if (word1.length != word2.length) return false

        val count1 = IntArray(26)
        val count2 = IntArray(26)
        val set1 = mutableSetOf<Char>()
        val set2 = mutableSetOf<Char>()

        for (ch in word1) {
            count1[ch - 'a']++
            set1.add(ch)
        }
        for (ch in word2) {
            count2[ch - 'a']++
            set2.add(ch)
        }

        count1.sort()
        count2.sort()
        return count1.contentEquals(count2) && set1 == set2
    }
}

fun main() {
    val word1 = "abc"
    val word2 = "bca"
    println(Solution().closeStrings(word1, word2)) // Output: true
}
```

### Dart

```dart
bool closeStrings(String word1, String word2) {
  if (word1.length != word2.length) return false;

  List<int> count1 = List.filled(26, 0);
  List<int> count2 = List.filled(26, 0);
  Set<String> set1 = {};
  Set<String> set2 = {};

  for (var ch in word1.runes) {
    count1[ch - 'a'.codeUnitAt(0)]++;
    set1.add(String.fromCharCode(ch));
  }
  for (var ch in word2.runes) {
    count2[ch - 'a'.codeUnitAt(0)]++;
    set2.add(String.fromCharCode(ch));
  }

  count1.sort();
  count2.sort();
  return count1.join() == count2.join() && set1 == set2;
}

void main() {
  print(closeStrings("abc", "bca")); // Output: true
}
```

### C#

```csharp
public class Solution {
    public bool CloseStrings(string word1, string word2) {
        if (word1.Length != word2.Length) return false;

        int[] count1 = new int[26];
        int[] count2 = new int[26];
        HashSet<char> set1 = new HashSet<char>();
        HashSet<char> set2 = new HashSet<char>();

        foreach (var ch in word1) {
            count1[ch - 'a']++;
            set1.Add(ch);
        }
        foreach (var ch in word2) {
            count2[ch - 'a']++;
            set2.Add(ch);
        }

        Array.Sort(count1);
        Array.Sort(count2);
        return count1.SequenceEqual(count2) && set1.SetEquals(set2);
    }
}
```

### Java

```java
class Solution {
    public boolean closeStrings(String word1, String word2) {
        if (word1.length() != word2.length()) return false;

        int[] count1 = new int[26];
        int[] count2 = new int[26];
        Set<Character> set1 = new HashSet<>();
        Set<Character> set2 = new HashSet<>();

        for (char ch : word1.toCharArray()) {
            count1[ch - 'a']++;
            set1.add(ch);
        }
        for (char ch : word2.toCharArray()) {
            count2[ch - 'a']++;
            set2.add(ch);
        }

        Arrays.sort(count1);
        Arrays.sort(count2);
        return Arrays.equals(count1, count2) && set1.equals(set2);
    }
}
```

### Swift

```swift
class Solution {
    func closeStrings(_ word1: String, _ word2: String) -> Bool {
        if word1.count != word2.count { return false }

        var count1 = [Int](repeating: 0, count: 26)
        var count2 = [Int](repeating: 0, count: 26)
        var set1 = Set<Character>()
        var set2 = Set<Character>()

        for ch in word1 {
            count1[Int(ch.asciiValue! - Character("a").asciiValue!)] += 1
            set1.insert(ch)
        }
        for ch in word2 {
            count2[Int(ch.asciiValue! - Character("a").asciiValue!)] += 1
            set2.insert(ch)
        }

        count1.sort()
        count2.sort()
        return count1 == count2 && set1 == set2
    }
}
```

### The End