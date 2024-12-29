# Lexicographically Smallest Equivalent String

## Problem Statement

You are given two strings `s1` and `s2` of the same length, and a string `baseStr`.  
Your task is to find the lexicographically smallest equivalent string of `baseStr` by replacing characters according to equivalence relationships defined by `s1` and `s2`.

## Input

```text
s1 = "parker", s2 = "morris", baseStr = "parser"
```

## Output

```text
"makkek"
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun smallestEquivalentString(s1: String, s2: String, baseStr: String): String {
        val roots = IntArray(26) { it }
        var root1: Int
        var root2: Int
        var newRoot: Int
        var rootToChange: Int
        for (i in s1.indices) {
            if (s1[i] == s2[i]) {
                continue
            }
            root1 = roots[s1[i] - 'a']
            root2 = roots[s2[i] - 'a']
            if (root1 < root2) {
                newRoot = root1
                rootToChange = root2
            } else {
                newRoot = root2
                rootToChange = root1
            }
            roots.forEachIndexed { index, root ->
                if (root == rootToChange) {
                    roots[index] = newRoot
                }
            }
        }

        val result = StringBuilder()
        baseStr.forEach {
            result.append('a' + roots[it - 'a'])
        }
        return result.toString()
    }
}
```

### Dart

```dart
String smallestEquivalentString(String s1, String s2, String baseStr) {
  List<int> roots = List<int>.generate(26, (index) => index);

  void union(int x, int y) {
    int rootX = find(x);
    int rootY = find(y);
    if (rootX < rootY) {
      for (int i = 0; i < 26; i++) {
        if (roots[i] == rootY) roots[i] = rootX;
      }
    } else {
      for (int i = 0; i < 26; i++) {
        if (roots[i] == rootX) roots[i] = rootY;
      }
    }
  }

  int find(int x) => roots[x];

  for (int i = 0; i < s1.length; i++) {
    union(s1.codeUnitAt(i) - 'a'.codeUnitAt(0), s2.codeUnitAt(i) - 'a'.codeUnitAt(0));
  }

  return String.fromCharCodes(baseStr.codeUnits.map((ch) => 'a'.codeUnitAt(0) + roots[ch - 'a'.codeUnitAt(0)]));
}
```

### C#

```csharp
public class Solution {
    public string SmallestEquivalentString(string s1, string s2, string baseStr) {
        int[] roots = new int[26];
        for (int i = 0; i < 26; i++) {
            roots[i] = i;
        }

        for (int i = 0; i < s1.Length; i++) {
            int root1 = Find(roots, s1[i] - 'a');
            int root2 = Find(roots, s2[i] - 'a');
            if (root1 != root2) {
                int smaller = Math.Min(root1, root2);
                int larger = Math.Max(root1, root2);
                for (int j = 0; j < 26; j++) {
                    if (roots[j] == larger) roots[j] = smaller;
                }
            }
        }

        char[] result = new char[baseStr.Length];
        for (int i = 0; i < baseStr.Length; i++) {
            result[i] = (char)('a' + roots[baseStr[i] - 'a']);
        }

        return new string(result);
    }

    private int Find(int[] roots, int x) {
        return roots[x];
    }
}
```

### Java

```java
class Solution {
    public String smallestEquivalentString(String s1, String s2, String baseStr) {
        int[] roots = new int[26];
        for (int i = 0; i < 26; i++) {
            roots[i] = i;
        }

        for (int i = 0; i < s1.length(); i++) {
            int root1 = find(roots, s1.charAt(i) - 'a');
            int root2 = find(roots, s2.charAt(i) - 'a');
            if (root1 != root2) {
                int smaller = Math.min(root1, root2);
                int larger = Math.max(root1, root2);
                for (int j = 0; j < 26; j++) {
                    if (roots[j] == larger) roots[j] = smaller;
                }
            }
        }

        StringBuilder result = new StringBuilder();
        for (char c : baseStr.toCharArray()) {
            result.append((char)('a' + roots[c - 'a']));
        }

        return result.toString();
    }

    private int find(int[] roots, int x) {
        return roots[x];
    }
}
```

### Swift

```swift
class Solution {
    func smallestEquivalentString(_ s1: String, _ s2: String, _ baseStr: String) -> String {
        var roots = Array(0..<26)

        func find(_ x: Int) -> Int {
            return roots[x]
        }

        for (c1, c2) in zip(s1, s2) {
            let root1 = find(Int(c1.asciiValue! - Character("a").asciiValue!))
            let root2 = find(Int(c2.asciiValue! - Character("a").asciiValue!))

            if root1 != root2 {
                let smaller = min(root1, root2)
                let larger = max(root1, root2)
                for i in 0..<26 {
                    if roots[i] == larger {
                        roots[i] = smaller
                    }
                }
            }
        }

        return baseStr.map { Character(UnicodeScalar("a".asciiValue! + UInt8(roots[Int($0.asciiValue! - Character("a").asciiValue!)]))) }.joined()
    }
}
```

### The End