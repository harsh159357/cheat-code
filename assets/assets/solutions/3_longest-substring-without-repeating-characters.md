# Longest Substring Without Repeating Characters

## Problem Statement

Given a string `s`, find the length of the longest substring without repeating characters.

## Input

```text
s = "abcabcbb"
```

## Output

```text
3  
(Explanation: The answer is "abc" with the length of 3.)
```

## Solutions

### Dart

```dart
int lengthOfLongestSubstring(String s) {
  int maxLength = 0;
  int left = 0;
  Map<String, int> charIndexMap = {};

  for (int right = 0; right < s.length; right++) {
    String char = s[right];

    if (charIndexMap.containsKey(char) && charIndexMap[char]! >= left) {
      left = charIndexMap[char]! + 1;
    }

    charIndexMap[char] = right;
    maxLength = maxLength > (right - left + 1) ? maxLength : (right - left + 1);
  }

  return maxLength;
}

void main() {
  print(lengthOfLongestSubstring("abcabcbb")); // Output: 3
  print(lengthOfLongestSubstring("bbbbb"));    // Output: 1
  print(lengthOfLongestSubstring("pwwkew"));   // Output: 3
}
```

### C#

```csharp
public class Solution {
    public int LengthOfLongestSubstring(string s) {
        int maxLength = 0;
        int left = 0;
        Dictionary<char, int> charIndexMap = new Dictionary<char, int>();

        for (int right = 0; right < s.Length; right++) {
            if (charIndexMap.ContainsKey(s[right]) && charIndexMap[s[right]] >= left) {
                left = charIndexMap[s[right]] + 1;
            }

            charIndexMap[s[right]] = right;
            maxLength = Math.Max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}

class Program {
    static void Main(string[] args) {
        Solution solution = new Solution();
        Console.WriteLine(solution.LengthOfLongestSubstring("abcabcbb")); // Output: 3
        Console.WriteLine(solution.LengthOfLongestSubstring("bbbbb"));    // Output: 1
        Console.WriteLine(solution.LengthOfLongestSubstring("pwwkew"));   // Output: 3
    }
}
```

### Java

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int maxLength = 0;
        int left = 0;
        Map<Character, Integer> charIndexMap = new HashMap<>();

        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);

            if (charIndexMap.containsKey(c) && charIndexMap.get(c) >= left) {
                left = charIndexMap.get(c) + 1;
            }

            charIndexMap.put(c, right);
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        System.out.println(solution.lengthOfLongestSubstring("abcabcbb")); // Output: 3
        System.out.println(solution.lengthOfLongestSubstring("bbbbb"));    // Output: 1
        System.out.println(solution.lengthOfLongestSubstring("pwwkew"));   // Output: 3
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun lengthOfLongestSubstring(s: String): Int {
        var maxLength = 0
        var left = 0
        val lastIndex = IntArray(128) { -1 } // Array to store the last index of each character

        for (right in s.indices) {
            val char = s[right]
            val lastIndexChar = lastIndex[char.toInt()]

            // Update left pointer if the current character was seen in the previous substring
            if (lastIndexChar != -1 && lastIndexChar >= left) {
                left = lastIndexChar + 1
            }

            // Update the last index of the current character
            lastIndex[char.toInt()] = right

            // Update the maximum length of the substring
            maxLength = maxOf(maxLength, right - left + 1)
        }

        return maxLength
    }
}

fun main() {
    val solution = Solution()

    // Test cases
    println(solution.lengthOfLongestSubstring("abcabcbb")) // Output: 3
    println(solution.lengthOfLongestSubstring("bbbbb"))    // Output: 1
    println(solution.lengthOfLongestSubstring("pwwkew"))   // Output: 3
}
```

### Swift

```swift
class Solution {
    func lengthOfLongestSubstring(_ s: String) -> Int {
        var maxLength = 0
        var left = 0
        var charIndexMap = [Character: Int]()

        for (right, char) in s.enumerated() {
            if let lastIndex = charIndexMap[char], lastIndex >= left {
                left = lastIndex + 1
            }

            charIndexMap[char] = right
            maxLength = max(maxLength, right - left + 1)
        }

        return maxLength
    }
}

let solution = Solution()
print(solution.lengthOfLongestSubstring("abcabcbb")) // Output: 3
print(solution.lengthOfLongestSubstring("bbbbb"))    // Output: 1
print(solution.lengthOfLongestSubstring("pwwkew"))   // Output: 3
```

### The End

