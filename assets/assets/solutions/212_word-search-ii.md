# Word Search II

## Problem Statement

Given an `m x n` board of characters and a list of strings `words`, find all the words in the list that can be constructed from letters of sequentially adjacent cells in the board. A word must be constructed using letters of sequentially adjacent cells, where "adjacent" cells are horizontally or vertically neighboring. The same letter cell may not be used more than once in a word.

## Input

```text
board = [
  ['o', 'a', 'a', 'n'],
  ['e', 't', 'a', 'e'],
  ['i', 'h', 'k', 'r'],
  ['i', 'f', 'l', 'v']
]
words = ["oath", "pea", "eat", "rain"]
```

## Output

```text
["oath", "eat"]
```

## Solutions

### Dart

```dart
class TrieNode {
  Map<String, TrieNode> children = {};
  String? word;
}

class Solution {
  List<String> findWords(List<List<String>> board, List<String> words) {
    final root = _buildTrie(words);
    final result = <String>[];

    void backtrack(TrieNode node, int row, int col) {
      final char = board[row][col];
      final nextNode = node.children[char];
      if (nextNode != null) {
        board[row][col] = '#';
        if (nextNode.word != null) {
          result.add(nextNode.word!);
          nextNode.word = null;
        }
        final dirs = [
          [-1, 0],
          [1, 0],
          [0, -1],
          [0, 1]
        ];
        for (var dir in dirs) {
          final newRow = row + dir[0];
          final newCol = col + dir[1];
          if (newRow >= 0 &&
              newRow < board.length &&
              newCol >= 0 &&
              newCol < board[0].length &&
              board[newRow][newCol] != '#') {
            backtrack(nextNode, newRow, newCol);
          }
        }
        board[row][col] = char;
      }
    }

    for (var i = 0; i < board.length; i++) {
      for (var j = 0; j < board[0].length; j++) {
        backtrack(root, i, j);
      }
    }
    return result;
  }

  TrieNode _buildTrie(List<String> words) {
    final root = TrieNode();
    for (var word in words) {
      var node = root;
      for (var char in word.split('')) {
        node.children.putIfAbsent(char, () => TrieNode());
        node = node.children[char]!;
      }
      node.word = word;
    }
    return root;
  }
}
```

### C#

```csharp
public class TrieNode {
    public Dictionary<char, TrieNode> Children = new();
    public string Word = null;
}

public class Solution {
    public IList<string> FindWords(char[][] board, string[] words) {
        TrieNode root = BuildTrie(words);
        var result = new List<string>();

        void Backtrack(TrieNode node, int row, int col) {
            char ch = board[row][col];
            if (!node.Children.ContainsKey(ch)) return;
            TrieNode nextNode = node.Children[ch];
            board[row][col] = '#';
            if (nextNode.Word != null) {
                result.Add(nextNode.Word);
                nextNode.Word = null;
            }
            foreach (var (dr, dc) in new[] { (-1, 0), (1, 0), (0, -1), (0, 1) }) {
                int newRow = row + dr, newCol = col + dc;
                if (newRow >= 0 && newRow < board.Length && newCol >= 0 && newCol < board[0].Length && board[newRow][newCol] != '#') {
                    Backtrack(nextNode, newRow, newCol);
                }
            }
            board[row][col] = ch;
        }

        for (int i = 0; i < board.Length; i++) {
            for (int j = 0; j < board[0].Length; j++) {
                Backtrack(root, i, j);
            }
        }
        return result;
    }

    private TrieNode BuildTrie(string[] words) {
        TrieNode root = new();
        foreach (var word in words) {
            TrieNode node = root;
            foreach (var c in word) {
                if (!node.Children.ContainsKey(c)) {
                    node.Children[c] = new TrieNode();
                }
                node = node.Children[c];
            }
            node.Word = word;
        }
        return root;
    }
}
```

### Java

```java
class TrieNode {
    Map<Character, TrieNode> children = new HashMap<>();
    String word = null;
}

class Solution {
    public List<String> findWords(char[][] board, String[] words) {
        TrieNode root = buildTrie(words);
        List<String> result = new ArrayList<>();

        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                backtrack(board, root, i, j, result);
            }
        }
        return result;
    }

    private void backtrack(char[][] board, TrieNode node, int row, int col, List<String> result) {
        char ch = board[row][col];
        if (!node.children.containsKey(ch)) return;

        TrieNode nextNode = node.children.get(ch);
        if (nextNode.word != null) {
            result.add(nextNode.word);
            nextNode.word = null;
        }

        board[row][col] = '#';
        int[][] dirs = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
        for (int[] dir : dirs) {
            int newRow = row + dir[0], newCol = col + dir[1];
            if (newRow >= 0 && newRow < board.length && newCol >= 0 && newCol < board[0].length && board[newRow][newCol] != '#') {
                backtrack(board, nextNode, newRow, newCol, result);
            }
        }
        board[row][col] = ch;
    }

    private TrieNode buildTrie(String[] words) {
        TrieNode root = new TrieNode();
        for (String word : words) {
            TrieNode node = root;
            for (char ch : word.toCharArray()) {
                node.children.putIfAbsent(ch, new TrieNode());
                node = node.children.get(ch);
            }
            node.word = word;
        }
        return root;
    }
}
```

### Swift

```swift
class TrieNode {
    var children: [Character: TrieNode] = [:]
    var word: String? = nil
}

class Solution {
    func findWords(_ board: [[Character]], _ words: [String]) -> [String] {
        let root = buildTrie(words)
        var result = [String]()
        var board = board

        func backtrack(_ node: TrieNode, _ row: Int, _ col: Int) {
            let ch = board[row][col]
            guard let nextNode = node.children[ch] else { return }

            board[row][col] = "#"
            if let word = nextNode.word {
                result.append(word)
                nextNode.word = nil
            }

            let directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]
            for (dr, dc) in directions {
                let newRow = row + dr, newCol = col + dc
                if newRow >= 0 && newRow < board.count && newCol >= 0 && newCol < board[0].count && board[newRow][newCol] != "#" {
                    backtrack(nextNode, newRow, newCol)
                }
            }

            board[row][col] = ch
        }

        for i in 0..<board.count {
            for j in 0..<board[0].count {
                backtrack(root, i, j)
            }
        }

        return result
    }

    private func buildTrie(_ words: [String]) -> TrieNode {
        let root = TrieNode()
        for word in words {
            var node = root
            for ch in word {
                if node.children[ch] == nil {
                    node.children[ch] = TrieNode()
                }
                node = node.children[ch]!
            }
            node.word = word
        }
        return root
    }
}
```

### The End

