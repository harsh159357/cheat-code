# Substring with Concatenation of All Words

## Problem Statement

You are given a string `s` and an array of strings `words`. All the strings of `words` are of the same length. Return all starting indices of substring(s) in `s` that is a concatenation of each word in `words` exactly once, in any order, and without any intervening characters.

## Input

```text
s = "barfoothefoobarman", words = ["foo", "bar"]
```

## Output

```text
[0, 9]
```

## Solutions

### Dart

```dart
List<int> findSubstring(String s, List<String> words) {
  if (s.isEmpty || words.isEmpty) return [];

  List<int> result = [];
  int wordLength = words[0].length;
  int wordCount = words.length;
  int totalLength = wordLength * wordCount;

  Map<String, int> wordMap = {};
  for (var word in words) {
    wordMap[word] = (wordMap[word] ?? 0) + 1;
  }

  for (int i = 0; i <= s.length - totalLength; i++) {
    Map<String, int> seen = {};
    int j = 0;

    while (j < wordCount) {
      String word = s.substring(i + j * wordLength, i + (j + 1) * wordLength);
      if (wordMap.containsKey(word)) {
        seen[word] = (seen[word] ?? 0) + 1;
        if (seen[word]! > wordMap[word]!) break;
      } else {
        break;
      }
      j++;
    }

    if (j == wordCount) result.add(i);
  }

  return result;
}

void main() {
  print(findSubstring("barfoothefoobarman", ["foo", "bar"])); // Output: [0, 9]
  print(findSubstring("wordgoodgoodgoodbestword", ["word", "good", "best", "word"])); // Output: []
  print(findSubstring("barfoofoobarthefoobarman", ["bar", "foo", "the"])); // Output: [6, 9, 12]
}
```

### C#

```csharp
public class Solution {
    public IList<int> FindSubstring(string s, string[] words) {
        if (s.Length == 0 || words.Length == 0) return new List<int>();

        var result = new List<int>();
        int wordLength = words[0].Length;
        int wordCount = words.Length;
        int totalLength = wordLength * wordCount;

        var wordMap = new Dictionary<string, int>();
        foreach (var word in words) {
            if (!wordMap.ContainsKey(word)) wordMap[word] = 0;
            wordMap[word]++;
        }

        for (int i = 0; i <= s.Length - totalLength; i++) {
            var seen = new Dictionary<string, int>();
            int j = 0;

            while (j < wordCount) {
                string word = s.Substring(i + j * wordLength, wordLength);
                if (wordMap.ContainsKey(word)) {
                    if (!seen.ContainsKey(word)) seen[word] = 0;
                    seen[word]++;
                    if (seen[word] > wordMap[word]) break;
                } else {
                    break;
                }
                j++;
            }

            if (j == wordCount) result.Add(i);
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        if (s.isEmpty() || words.length == 0) return new ArrayList<>();

        List<Integer> result = new ArrayList<>();
        int wordLength = words[0].length();
        int wordCount = words.length;
        int totalLength = wordLength * wordCount;

        Map<String, Integer> wordMap = new HashMap<>();
        for (String word : words) {
            wordMap.put(word, wordMap.getOrDefault(word, 0) + 1);
        }

        for (int i = 0; i <= s.length() - totalLength; i++) {
            Map<String, Integer> seen = new HashMap<>();
            int j = 0;

            while (j < wordCount) {
                String word = s.substring(i + j * wordLength, i + (j + 1) * wordLength);
                if (wordMap.containsKey(word)) {
                    seen.put(word, seen.getOrDefault(word, 0) + 1);
                    if (seen.get(word) > wordMap.get(word)) break;
                } else {
                    break;
                }
                j++;
            }

            if (j == wordCount) result.add(i);
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun findSubstring(s: String, words: Array<String>): List<Int> {
        if (s.isEmpty() || words.isEmpty()) return emptyList()

        val result = mutableListOf<Int>()
        val wordLength = words[0].length
        val wordCount = words.size
        val totalLength = wordLength * wordCount
        val wordMap = mutableMapOf<String, Int>()

        for (word in words) {
            wordMap[word] = wordMap.getOrDefault(word, 0) + 1
        }

        for (i in 0..s.length - totalLength) {
            val seen = mutableMapOf<String, Int>()
            var j = 0
            while (j < wordCount) {
                val word = s.substring(i + j * wordLength, i + (j + 1) * wordLength)
                if (wordMap.containsKey(word)) {
                    seen[word] = seen.getOrDefault(word, 0) + 1
                    if (seen[word]!! > wordMap[word]!!) break
                } else {
                    break
                }
                j++
            }
            if (j == wordCount) result.add(i)
        }

        return result
    }
}

fun main() {
    val s1 = "barfoothefoobarman"
    val words1 = arrayOf("foo", "bar")
    println(Solution().findSubstring(s1, words1)) // Output: [0, 9]

    val s2 = "wordgoodgoodgoodbestword"
    val words2 = arrayOf("word", "good", "best", "word")
    println(Solution().findSubstring(s2, words2)) // Output: []

    val s3 = "barfoofoobarthefoobarman"
    val words3 = arrayOf("bar", "foo", "the")
    println(Solution().findSubstring(s3, words3)) // Output: [6, 9, 12]
}
```

### Swift

```swift
class Solution {
    func findSubstring(_ s: String, _ words: [String]) -> [Int] {
        if s.isEmpty || words.isEmpty { return [] }

        var result: [Int] = []
        let wordLength = words[0].count
        let wordCount = words.count
        let totalLength = wordLength * wordCount

        var wordMap: [String: Int] = [:]
        for word in words {
            wordMap[word, default: 0] += 1
        }

        for i in 0...(s.count - totalLength) {
            var seen: [String: Int] = [:]
            var j = 0

            while j < wordCount {
                let start = s.index(s.startIndex, offsetBy: i + j * wordLength)
                let end = s.index(start, offsetBy: wordLength)
                let word = String(s[start..<end])

                if let count = wordMap[word] {
                    seen[word, default: 0] += 1
                    if seen[word]! > count { break }
                } else {
                    break
                }

                j += 1
            }

            if j == wordCount {
                result.append(i)
            }
        }

        return result
    }
}

let solution = Solution()
print(solution.findSubstring("barfoothefoobarman", ["foo", "bar"])) // Output: [0, 9]
print(solution.findSubstring("wordgoodgoodgoodbestword", ["word", "good", "best", "word"])) // Output: []
print(solution.findSubstring("barfoofoobarthefoobarman", ["bar", "foo", "the"])) // Output: [6, 9, 12]
```


### The End

