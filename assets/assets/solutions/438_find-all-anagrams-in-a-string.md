# Find All Anagrams in a String

## Problem Statement

Given two strings `s` and `p`, return an array of all the start indices of `p`'s anagrams in `s`. You may return the answer in any order.

An anagram is a permutation of a string. For example, `"abc"` is an anagram of `"cba"`, and `"abcd"` is an anagram of `"dbca"`.

## Input

```text
s = "cbaebabacd"
p = "abc"
```

## Output

```text
[0, 6]
```

## Solutions

### Dart

```dart
List<int> findAnagrams(String s, String p) {
  List<int> result = [];
  Map<String, int> targetMap = {};
  Map<String, int> windowMap = {};

  // Populate the frequency map for the target string
  for (var char in p.split('')) {
    targetMap[char] = (targetMap[char] ?? 0) + 1;
  }

  int left = 0, right = 0, matched = 0;

  // Move the sliding window
  while (right < s.length) {
    String charRight = s[right];

    // Expand the window
    windowMap[charRight] = (windowMap[charRight] ?? 0) + 1;

    if (windowMap[charRight] == targetMap[charRight]) {
      matched++;
    }

    // Shrink the window
    if (right - left + 1 > p.length) {
      String charLeft = s[left];
      if (windowMap[charLeft] == targetMap[charLeft]) {
        matched--;
      }
      windowMap[charLeft] = (windowMap[charLeft] ?? 0) - 1;
      left++;
    }

    // Check for a valid anagram
    if (matched == targetMap.length) {
      result.add(left);
    }

    right++;
  }

  return result;
}
```

### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public IList<int> FindAnagrams(string s, string p) {
        var result = new List<int>();
        var targetMap = new Dictionary<char, int>();
        var windowMap = new Dictionary<char, int>();

        foreach (var charP in p) {
            if (!targetMap.ContainsKey(charP)) targetMap[charP] = 0;
            targetMap[charP]++;
        }

        int left = 0, right = 0, matched = 0;

        while (right < s.Length) {
            char charRight = s[right];
            if (!windowMap.ContainsKey(charRight)) windowMap[charRight] = 0;
            windowMap[charRight]++;

            if (windowMap[charRight] == targetMap.GetValueOrDefault(charRight)) {
                matched++;
            }

            if (right - left + 1 > p.Length) {
                char charLeft = s[left];
                if (windowMap[charLeft] == targetMap.GetValueOrDefault(charLeft)) {
                    matched--;
                }
                windowMap[charLeft]--;
                left++;
            }

            if (matched == targetMap.Count) {
                result.Add(left);
            }

            right++;
        }

        return result;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> result = new ArrayList<>();
        Map<Character, Integer> targetMap = new HashMap<>();
        Map<Character, Integer> windowMap = new HashMap<>();

        for (char ch : p.toCharArray()) {
            targetMap.put(ch, targetMap.getOrDefault(ch, 0) + 1);
        }

        int left = 0, right = 0, matched = 0;

        while (right < s.length()) {
            char charRight = s.charAt(right);
            windowMap.put(charRight, windowMap.getOrDefault(charRight, 0) + 1);

            if (windowMap.get(charRight).equals(targetMap.get(charRight))) {
                matched++;
            }

            if (right - left + 1 > p.length()) {
                char charLeft = s.charAt(left);
                if (windowMap.get(charLeft).equals(targetMap.get(charLeft))) {
                    matched--;
                }
                windowMap.put(charLeft, windowMap.get(charLeft) - 1);
                left++;
            }

            if (matched == targetMap.size()) {
                result.add(left);
            }

            right++;
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun findAnagrams(s: String, p: String): List<Int> {
        val result = mutableListOf<Int>()
        val targetMap = mutableMapOf<Char, Int>()
        val windowMap = mutableMapOf<Char, Int>()

        for (char in p) {
            targetMap[char] = targetMap.getOrDefault(char, 0) + 1
        }

        var left = 0
        var right = 0
        var matched = 0

        while (right < s.length) {
            val charRight = s[right]
            windowMap[charRight] = windowMap.getOrDefault(charRight, 0) + 1

            if (windowMap[charRight] == targetMap[charRight]) {
                matched++
            }

            if (right - left + 1 > p.length) {
                val charLeft = s[left]
                if (windowMap[charLeft] == targetMap[charLeft]) {
                    matched--
                }
                windowMap[charLeft] = windowMap.getOrDefault(charLeft, 0) - 1
                left++
            }

            if (matched == targetMap.size) {
                result.add(left)
            }

            right++
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func findAnagrams(_ s: String, _ p: String) -> [Int] {
        var result = [Int]()
        var targetMap = [Character: Int]()
        var windowMap = [Character: Int]()

        for char in p {
            targetMap[char, default: 0] += 1
        }

        var left = 0, right = 0, matched = 0
        let sArray = Array(s)

        while right < sArray.count {
            let charRight = sArray[right]
            windowMap[charRight, default: 0] += 1

            if windowMap[charRight] == targetMap[charRight] {
                matched += 1
            }

            if right - left + 1 > p.count {
                let charLeft = sArray[left]
                if windowMap[charLeft] == targetMap[charLeft] {
                    matched -= 1
                }
                windowMap[charLeft, default: 0] -= 1
                left += 1
            }

            if matched == targetMap.count {
                result.append(left)
            }

            right += 1
        }

        return result
    }
}
```

### The End