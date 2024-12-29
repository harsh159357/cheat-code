# Word Ladder

## Problem Statement

Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return the length of the shortest transformation sequence from `beginWord` to `endWord`, such that:

1. Only one letter can be changed at a time.
2. Each transformed word must exist in the word list.

Note: Return `0` if there is no such transformation sequence.

---

## Input

```text
beginWord = "hit"
endWord = "cog"
wordList = ["hot", "dot", "dog", "lot", "log", "cog"]
```

## Output

```text
5
```


## Solutions

### Dart

```dart
import 'dart:collection';

int ladderLength(String beginWord, String endWord, List<String> wordList) {
  final wordSet = wordList.toSet();
  if (!wordSet.contains(endWord)) return 0;

  final queue = Queue<String>();
  queue.add(beginWord);
  final visited = <String>{beginWord};
  int steps = 1;

  while (queue.isNotEmpty) {
    final size = queue.length;
    for (int i = 0; i < size; i++) {
      final current = queue.removeFirst();
      final charArray = current.split('');
      for (int j = 0; j < charArray.length; j++) {
        final originalChar = charArray[j];
        for (int k = 0; k < 26; k++) {
          charArray[j] = String.fromCharCode(97 + k);
          final newWord = charArray.join('');
          if (newWord == endWord) return steps + 1;
          if (wordSet.contains(newWord) && !visited.contains(newWord)) {
            queue.add(newWord);
            visited.add(newWord);
          }
        }
        charArray[j] = originalChar;
      }
    }
    steps++;
  }
  return 0;
}
```


### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public int LadderLength(string beginWord, string endWord, IList<string> wordList) {
        var wordSet = new HashSet<string>(wordList);
        if (!wordSet.Contains(endWord)) return 0;

        var queue = new Queue<string>();
        queue.Enqueue(beginWord);
        var visited = new HashSet<string> { beginWord };
        int steps = 1;

        while (queue.Count > 0) {
            int size = queue.Count;
            for (int i = 0; i < size; i++) {
                var current = queue.Dequeue();
                var charArray = current.ToCharArray();
                for (int j = 0; j < charArray.Length; j++) {
                    char originalChar = charArray[j];
                    for (char k = 'a'; k <= 'z'; k++) {
                        if (k == originalChar) continue;
                        charArray[j] = k;
                        var newWord = new string(charArray);
                        if (newWord == endWord) return steps + 1;
                        if (wordSet.Contains(newWord) && !visited.Contains(newWord)) {
                            queue.Enqueue(newWord);
                            visited.Add(newWord);
                        }
                    }
                    charArray[j] = originalChar;
                }
            }
            steps++;
        }
        return 0;
    }
}
```


### Java

```java
import java.util.*;

class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        Set<String> wordSet = new HashSet<>(wordList);
        if (!wordSet.contains(endWord)) return 0;

        Queue<String> queue = new LinkedList<>();
        queue.offer(beginWord);
        Set<String> visited = new HashSet<>();
        visited.add(beginWord);
        int steps = 1;

        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                String current = queue.poll();
                char[] charArray = current.toCharArray();
                for (int j = 0; j < charArray.length; j++) {
                    char originalChar = charArray[j];
                    for (char k = 'a'; k <= 'z'; k++) {
                        if (k == originalChar) continue;
                        charArray[j] = k;
                        String newWord = new String(charArray);
                        if (newWord.equals(endWord)) return steps + 1;
                        if (wordSet.contains(newWord) && !visited.contains(newWord)) {
                            queue.offer(newWord);
                            visited.add(newWord);
                        }
                    }
                    charArray[j] = originalChar;
                }
            }
            steps++;
        }
        return 0;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun ladderLength(beginWord: String, endWord: String, wordList: List<String>): Int {
        val wordSet = wordList.toHashSet()
        if (endWord !in wordSet) return 0

        val queue = LinkedList<String>()
        queue.offer(beginWord)
        val visited = mutableSetOf<String>()
        visited.add(beginWord)
        var steps = 1

        while (queue.isNotEmpty()) {
            repeat(queue.size) {
                val current = queue.poll()
                val charArray = current.toCharArray()
                for (j in charArray.indices) {
                    val originalChar = charArray[j]
                    for (k in 'a'..'z') {
                        if (k == originalChar) continue
                        charArray[j] = k
                        val newWord = String(charArray)
                        if (newWord == endWord) return steps + 1
                        if (newWord in wordSet && newWord !in visited) {
                            queue.offer(newWord)
                            visited.add(newWord)
                        }
                    }
                    charArray[j] = originalChar
                }
            }
            steps++
        }
        return 0
    }
}
```

### Swift

```swift
class Solution {
    func ladderLength(_ beginWord: String, _ endWord: String, _ wordList: [String]) -> Int {
        var wordSet = Set(wordList)
        if !wordSet.contains(endWord) { return 0 }

        var queue = [beginWord]
        var visited = Set<String>([beginWord])
        var steps = 1

        while !queue.isEmpty {
            let size = queue.count
            for _ in 0..<size {
                let current = queue.removeFirst()
                var charArray = Array(current)
                for i in 0..<charArray.count {
                    let originalChar = charArray[i]
                    for char in "abcdefghijklmnopqrstuvwxyz" {
                        charArray[i] = char
                        let newWord = String(charArray)
                        if newWord == endWord { return steps + 1 }
                        if wordSet.contains(newWord) && !visited.contains(newWord) {
                            queue.append(newWord)
                            visited.insert(newWord)
                        }
                    }
                    charArray[i] = originalChar
                }
            }
            steps += 1
        }
        return 0
    }
}
```


### The End

