# Implement Trie (Prefix Tree)

## Problem Statement

A **Trie** (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are three main operations:

1. **Insert** a word into the Trie.
2. **Search** for a word in the Trie.
3. Check if there is any word in the Trie that starts with a given **prefix**.

Implement a `Trie` class with the following methods:

- `insert(word: String)`: Inserts the string `word` into the Trie.
- `search(word: String): Boolean`: Returns `true` if the string `word` is in the Trie, otherwise `false`.
- `startsWith(prefix: String): Boolean`: Returns `true` if there is any string in the Trie that starts with the string `prefix`.

## Input

```text
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
```

## Output

```text
[null, null, true, false, true, null, true]
```

## Solutions

### Dart

```dart
class TrieNode {
  Map<String, TrieNode> children = {};
  bool isEndOfWord = false;
}

class Trie {
  final TrieNode root = TrieNode();

  void insert(String word) {
    TrieNode node = root;
    for (int i = 0; i < word.length; i++) {
      String char = word[i];
      node.children.putIfAbsent(char, () => TrieNode());
      node = node.children[char]!;
    }
    node.isEndOfWord = true;
  }

  bool search(String word) {
    TrieNode? node = findNode(word);
    return node != null && node.isEndOfWord;
  }

  bool startsWith(String prefix) {
    return findNode(prefix) != null;
  }

  TrieNode? findNode(String prefix) {
    TrieNode node = root;
    for (int i = 0; i < prefix.length; i++) {
      String char = prefix[i];
      if (!node.children.containsKey(char)) {
        return null;
      }
      node = node.children[char]!;
    }
    return node;
  }
}
```

### C#

```csharp
public class TrieNode {
    public Dictionary<char, TrieNode> Children = new();
    public bool IsEndOfWord = false;
}

public class Trie {
    private readonly TrieNode root = new();

    public void Insert(string word) {
        TrieNode node = root;
        foreach (char ch in word) {
            if (!node.Children.ContainsKey(ch)) {
                node.Children[ch] = new TrieNode();
            }
            node = node.Children[ch];
        }
        node.IsEndOfWord = true;
    }

    public bool Search(string word) {
        TrieNode node = FindNode(word);
        return node != null && node.IsEndOfWord;
    }

    public bool StartsWith(string prefix) {
        return FindNode(prefix) != null;
    }

    private TrieNode FindNode(string prefix) {
        TrieNode node = root;
        foreach (char ch in prefix) {
            if (!node.Children.ContainsKey(ch)) {
                return null;
            }
            node = node.Children[ch];
        }
        return node;
    }
}
```

### Java

```java
class TrieNode {
    Map<Character, TrieNode> children = new HashMap<>();
    boolean isEndOfWord = false;
}

class Trie {
    private final TrieNode root = new TrieNode();

    public void insert(String word) {
        TrieNode node = root;
        for (char ch : word.toCharArray()) {
            node.children.putIfAbsent(ch, new TrieNode());
            node = node.children.get(ch);
        }
        node.isEndOfWord = true;
    }

    public boolean search(String word) {
        TrieNode node = findNode(word);
        return node != null && node.isEndOfWord;
    }

    public boolean startsWith(String prefix) {
        return findNode(prefix) != null;
    }

    private TrieNode findNode(String prefix) {
        TrieNode node = root;
        for (char ch : prefix.toCharArray()) {
            if (!node.children.containsKey(ch)) {
                return null;
            }
            node = node.children.get(ch);
        }
        return node;
    }
}
```

### Kotlin

```kotlin
class TrieNode {
    val children = HashMap<Char, TrieNode>()
    var isEndOfWord = false
}

class Trie {
    private val root = TrieNode()

    fun insert(word: String) {
        var node = root
        for (ch in word) {
            if (!node.children.containsKey(ch)) {
                node.children[ch] = TrieNode()
            }
            node = node.children[ch]!!
        }
        node.isEndOfWord = true
    }

    fun search(word: String): Boolean {
        var node = root
        for (ch in word) {
            if (!node.children.containsKey(ch)) {
                return false
            }
            node = node.children[ch]!!
        }
        return node.isEndOfWord
    }

    fun startsWith(prefix: String): Boolean {
        var node = root
        for (ch in prefix) {
            if (!node.children.containsKey(ch)) {
                return false
            }
            node = node.children[ch]!!
        }
        return true
    }
}
```

### Swift

```swift
class TrieNode {
    var children: [Character: TrieNode] = [:]
    var isEndOfWord: Bool = false
}

class Trie {
    private let root = TrieNode()

    func insert(_ word: String) {
        var node = root
        for char in word {
            if node.children[char] == nil {
                node.children[char] = TrieNode()
            }
            node = node.children[char]!
        }
        node.isEndOfWord = true
    }

    func search(_ word: String) -> Bool {
        guard let node = findNode(word) else { return false }
        return node.isEndOfWord
    }

    func startsWith(_ prefix: String) -> Bool {
        return findNode(prefix) != nil
    }

    private func findNode(_ prefix: String) -> TrieNode? {
        var node = root
        for char in prefix {
            guard let nextNode = node.children[char] else { return nil }
            node = nextNode
        }
        return node
    }
}
```

### The End

