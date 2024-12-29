# Minimum Window Substring

## Problem Statement

Given two strings `s` and `t` of lengths `m` and `n` respectively, find the minimum window in `s` that will contain all the characters in `t`. If there is no such window in `s` that covers all characters in `t`, return the empty string `""`.

## Input

```text
s = "ADOBECODEBANC"
t = "ABC"
```

## Output

```text
"BANC"
(Explanation: The substring "BANC" is the smallest substring in `s` that contains all characters of `t`.)
```

## Solutions

### Dart

```dart
String minWindow(String s, String t) {
  if (t.isEmpty || s.isEmpty) return "";
  
  Map<String, int> tMap = {};
  Map<String, int> sMap = {};
  
  for (var char in t.split('')) {
    tMap[char] = (tMap[char] ?? 0) + 1;
  }
  
  int left = 0, minStart = 0, minLength = s.length + 1, count = 0;
  
  for (int right = 0; right < s.length; right++) {
    String char = s[right];
    if (tMap.containsKey(char)) {
      sMap[char] = (sMap[char] ?? 0) + 1;
      if (sMap[char] == tMap[char]) count++;
    }
    
    while (count == tMap.length) {
      if (right - left + 1 < minLength) {
        minStart = left;
        minLength = right - left + 1;
      }
      String leftChar = s[left];
      if (tMap.containsKey(leftChar)) {
        sMap[leftChar] = sMap[leftChar]! - 1;
        if (sMap[leftChar]! < tMap[leftChar]!) count--;
      }
      left++;
    }
  }
  
  return minLength > s.length ? "" : s.substring(minStart, minStart + minLength);
}

void main() {
  print(minWindow("ADOBECODEBANC", "ABC")); // Output: "BANC"
  print(minWindow("a", "a")); // Output: "a"
  print(minWindow("a", "aa")); // Output: ""
}
```

### C#

```csharp
public class Solution {
    public string MinWindow(string s, string t) {
        if (t.Length > s.Length) return "";

        var tMap = new Dictionary<char, int>();
        foreach (char c in t) {
            if (!tMap.ContainsKey(c)) tMap[c] = 0;
            tMap[c]++;
        }

        var sMap = new Dictionary<char, int>();
        int left = 0, count = 0, minStart = 0, minLen = int.MaxValue;

        for (int right = 0; right < s.Length; right++) {
            char c = s[right];
            if (tMap.ContainsKey(c)) {
                if (!sMap.ContainsKey(c)) sMap[c] = 0;
                sMap[c]++;
                if (sMap[c] == tMap[c]) count++;
            }

            while (count == tMap.Count) {
                if (right - left + 1 < minLen) {
                    minLen = right - left + 1;
                    minStart = left;
                }

                char leftChar = s[left];
                if (tMap.ContainsKey(leftChar)) {
                    sMap[leftChar]--;
                    if (sMap[leftChar] < tMap[leftChar]) count--;
                }
                left++;
            }
        }

        return minLen == int.MaxValue ? "" : s.Substring(minStart, minLen);
    }
}
```

### Java

```java
class Solution {
    public String minWindow(String s, String t) {
        if (t.length() > s.length()) return "";

        Map<Character, Integer> tMap = new HashMap<>();
        for (char c : t.toCharArray()) {
            tMap.put(c, tMap.getOrDefault(c, 0) + 1);
        }

        Map<Character, Integer> sMap = new HashMap<>();
        int left = 0, count = 0, minStart = 0, minLen = Integer.MAX_VALUE;

        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            if (tMap.containsKey(c)) {
                sMap.put(c, sMap.getOrDefault(c, 0) + 1);
                if (sMap.get(c).equals(tMap.get(c))) count++;
            }

            while (count == tMap.size()) {
                if (right - left + 1 < minLen) {
                    minLen = right - left + 1;
                    minStart = left;
                }

                char leftChar = s.charAt(left);
                if (tMap.containsKey(leftChar)) {
                    sMap.put(leftChar, sMap.get(leftChar) - 1);
                    if (sMap.get(leftChar) < tMap.get(leftChar)) count--;
                }
                left++;
            }
        }

        return minLen == Integer.MAX_VALUE ? "" : s.substring(minStart, minStart + minLen);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun minWindow(s: String, t: String): String {
        val sMap = mutableMapOf<Char, Int>()
        val tMap = mutableMapOf<Char, Int>()

        for (char in t) {
            tMap[char] = tMap.getOrDefault(char, 0) + 1
        }

        var left = 0
        var minLen = Int.MAX_VALUE
        var minStart = 0
        var count = 0

        for (right in s.indices) {
            val char = s[right]
            if (char in tMap) {
                sMap[char] = sMap.getOrDefault(char, 0) + 1
                if (sMap[char] == tMap[char]) count++
            }

            while (count == tMap.size) {
                if (right - left + 1 < minLen) {
                    minLen = right - left + 1
                    minStart = left
                }
                val leftChar = s[left]
                if (leftChar in tMap) {
                    sMap[leftChar] = sMap[leftChar]!! - 1
                    if (sMap[leftChar]!! < tMap[leftChar]!!) count--
                }
                left++
            }
        }

        return if (minLen == Int.MAX_VALUE) "" else s.substring(minStart, minStart + minLen)
    }
}
```

### Swift

```swift
class Solution {
    func minWindow(_ s: String, _ t: String) -> String {
        var tMap = [Character: Int]()
        for char in t { tMap[char, default: 0] += 1 }
        
        var sMap = [Character: Int]()
        var left = 0
        var minLen = Int.max
        var minStart = 0
        var count = 0
        
        for (right, char) in s.enumerated() {
            if let _ = tMap[char] {
                sMap[char, default: 0] += 1
                if sMap[char] == tMap[char] { count += 1 }
            }
            
            while count == tMap.count {
                if right - left + 1 < minLen {
                    minLen = right - left + 1
                    minStart = left
                }
                let leftChar = s[s.index(s.startIndex, offsetBy: left)]
                if let _ = tMap[leftChar] {
                    sMap[leftChar]! -= 1
                    if sMap[leftChar]! < tMap[leftChar]! { count -= 1 }
                }
                left += 1
            }
        }
        
        return minLen == Int.max ? "" : String(s[s.index(s.startIndex, offsetBy: minStart)..<s.index(s.startIndex, offsetBy: minStart + minLen)])
    }
}
```

### The End

