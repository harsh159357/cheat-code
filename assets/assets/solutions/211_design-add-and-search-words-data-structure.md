# Design Add and Search Words Data Structure

## Problem Statement

Design a data structure that supports adding new words and searching for a string, where the string may contain dots (`.`) as wildcards. Each dot can represent any letter.

Implement the following methods:
- `addWord(word)`: Adds a word into the data structure.
- `search(word)`: Searches a word in the data structure, allowing dots to act as wildcards.

## Input

```text
["WordDictionary", "addWord", "addWord", "addWord", "search", "search", "search", "search"]
[[], ["bad"], ["dad"], ["mad"], ["pad"], ["bad"], [".ad"], ["b.."]]
```

## Output

```text
[null, null, null, null, false, true, true, true]
```

## Solutions

### Dart

```dart
class TrieNode {
  bool isWord = false;
  List<TrieNode?> children = List.filled(26, null);
}

class WordDictionary {
  final TrieNode root = TrieNode();

  void addWord(String word) {
    TrieNode current = root;
    for (var i = 0; i < word.length; i++) {
      int index = word.codeUnitAt(i) - 'a'.codeUnitAt(0);
      current.children[index] ??= TrieNode();
      current = current.children[index]!;
    }
    current.isWord = true;
  }

  bool search(String word) => _searchRec(root, word, 0);

  bool _searchRec(TrieNode node, String word, int index) {
    if (index == word.length) return node.isWord;
    char c = word[index];
    if (c == '.') {
      return node.children.any((child) => child != null && _searchRec(child!, word, index + 1));
    } else {
      int idx = c.codeUnitAt(0) - 'a'.codeUnitAt(0);
      return node.children[idx]?.let((child) => _searchRec(child, word, index + 1)) ?? false;
    }
  }
}
```

### C#

```csharp
public class TrieNode {
    public bool IsWord = false;
    public TrieNode[] Children = new TrieNode[26];
}

public class WordDictionary {
    private readonly TrieNode root = new TrieNode();

    public void AddWord(string word) {
        TrieNode current = root;
        foreach (char c in word) {
            int index = c - 'a';
            if (current.Children[index] == null) {
                current.Children[index] = new TrieNode();
            }
            current = current.Children[index];
        }
        current.IsWord = true;
    }

    public bool Search(string word) {
        return SearchRec(root, word, 0);
    }

    private bool SearchRec(TrieNode node, string word, int index) {
        if (index == word.Length) return node.IsWord;
        char c = word[index];
        if (c == '.') {
            foreach (var child in node.Children) {
                if (child != null && SearchRec(child, word, index + 1)) return true;
            }
            return false;
        } else {
            int idx = c - 'a';
            return node.Children[idx] != null && SearchRec(node.Children[idx], word, index + 1);
        }
    }
}
```

### Java

```java
class TrieNode {
    boolean isWord = false;
    TrieNode[] children = new TrieNode[26];
}

class WordDictionary {
    private final TrieNode root = new TrieNode();

    public void addWord(String word) {
        TrieNode current = root;
        for (char c : word.toCharArray()) {
            int index = c - 'a';
            if (current.children[index] == null) {
                current.children[index] = new TrieNode();
            }
            current = current.children[index];
        }
        current.isWord = true;
    }

    public boolean search(String word) {
        return searchRec(root, word, 0);
    }

    private boolean searchRec(TrieNode node, String word, int index) {
        if (index == word.length()) return node.isWord;
        char c = word.charAt(index);
        if (c == '.') {
            for (TrieNode child : node.children) {
                if (child != null && searchRec(child, word, index + 1)) return true;
            }
            return false;
        } else {
            int idx = c - 'a';
            return node.children[idx] != null && searchRec(node.children[idx], word, index + 1);
        }
    }
}
```

### Kotlin

```kotlin
class TrieNode {
    var isWord = false
    val children = Array<TrieNode?>(26) { null }
}

class WordDictionary {
    private val root = TrieNode()

    fun addWord(word: String) {
        var current = root
        for (char in word) {
            val index = char - 'a'
            if (current.children[index] == null) {
                current.children[index] = TrieNode()
            }
            current = current.children[index]!!
        }
        current.isWord = true
    }

    fun search(word: String): Boolean = searchRec(root, word, 0)

    private fun searchRec(node: TrieNode, word: String, index: Int): Boolean {
        if (index == word.length) return node.isWord
        val char = word[index]
        return if (char == '.') {
            node.children.any { it != null && searchRec(it!!, word, index + 1) }
        } else {
            node.children[char - 'a']?.let { searchRec(it, word, index + 1) } ?: false
        }
    }
}
```

### Swift

```swift
class TrieNode {
    var isWord = false
    var children = [Character: TrieNode]()
}

class WordDictionary {
    private let root = TrieNode()

    func addWord(_ word: String) {
        var current = root
        for char in word {
            if current.children[char] == nil {
                current.children[char] = TrieNode()
            }
            current = current.children[char]!
        }
        current.isWord = true
    }

    func search(_ word: String) -> Bool {
        return searchRec(root, Array(word), 0)
    }

    private func searchRec(_ node: TrieNode, _ word: [Character], _ index: Int) -> Bool {
        if index == word.count { return node.isWord }
        let char = word[index]
        if char == "." {
            return node.children.values.contains { searchRec($0, word, index + 1) }
        } else {
            return node.children[char].map { searchRec($0, word, index + 1) } ?? false
        }
    }
}
```


### The End

