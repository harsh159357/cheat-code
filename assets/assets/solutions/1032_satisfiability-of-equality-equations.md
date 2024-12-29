# Satisfiability of Equality Equations

## Problem Statement

You are given an array of strings `equations` that represent relationships between variables. Each string is of length `4` and represents an equation or inequality:

- `"a==b"` means `a` is equal to `b`.
- `"a!=b"` means `a` is not equal to `b`.

Return `true` if all the equations can be satisfied, and `false` otherwise.

## Input

```text
equations = ["a==b", "b!=c", "c==a"]
```

## Output

```text
false
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun equationsPossible(equations: Array<String>): Boolean {
        val uf = UnionFind(26)

        // Process all equality equations
        for (equation in equations) {
            if (equation[1] == '=') {
                val x = equation[0] - 'a'
                val y = equation[3] - 'a'
                uf.union(x, y)
            }
        }

        // Check inequality equations
        for (equation in equations) {
            if (equation[1] == '!') {
                val x = equation[0] - 'a'
                val y = equation[3] - 'a'
                if (uf.find(x) == uf.find(y)) {
                    return false
                }
            }
        }

        return true
    }

    class UnionFind(n: Int) {
        private val parent = IntArray(n) { it }

        fun find(x: Int): Int {
            if (parent[x] != x) {
                parent[x] = find(parent[x])
            }
            return parent[x]
        }

        fun union(x: Int, y: Int) {
            parent[find(x)] = find(y)
        }
    }
}
```

### Dart

```dart
class UnionFind {
  final List<int> parent;

  UnionFind(int n) : parent = List.generate(n, (index) => index);

  int find(int x) {
    if (parent[x] != x) {
      parent[x] = find(parent[x]);
    }
    return parent[x];
  }

  void union(int x, int y) {
    parent[find(x)] = find(y);
  }
}

bool equationsPossible(List<String> equations) {
  final uf = UnionFind(26);

  // Process all equality equations
  for (final equation in equations) {
    if (equation[1] == '=') {
      final x = equation.codeUnitAt(0) - 'a'.codeUnitAt(0);
      final y = equation.codeUnitAt(3) - 'a'.codeUnitAt(0);
      uf.union(x, y);
    }
  }

  // Check inequality equations
  for (final equation in equations) {
    if (equation[1] == '!') {
      final x = equation.codeUnitAt(0) - 'a'.codeUnitAt(0);
      final y = equation.codeUnitAt(3) - 'a'.codeUnitAt(0);
      if (uf.find(x) == uf.find(y)) {
        return false;
      }
    }
  }

  return true;
}
```

### C#

```csharp
public class Solution {
    public bool EquationsPossible(string[] equations) {
        var uf = new UnionFind(26);

        // Process all equality equations
        foreach (var equation in equations) {
            if (equation[1] == '=') {
                int x = equation[0] - 'a';
                int y = equation[3] - 'a';
                uf.Union(x, y);
            }
        }

        // Check inequality equations
        foreach (var equation in equations) {
            if (equation[1] == '!') {
                int x = equation[0] - 'a';
                int y = equation[3] - 'a';
                if (uf.Find(x) == uf.Find(y)) {
                    return false;
                }
            }
        }

        return true;
    }

    private class UnionFind {
        private int[] parent;

        public UnionFind(int n) {
            parent = new int[n];
            for (int i = 0; i < n; i++) {
                parent[i] = i;
            }
        }

        public int Find(int x) {
            if (parent[x] != x) {
                parent[x] = Find(parent[x]);
            }
            return parent[x];
        }

        public void Union(int x, int y) {
            parent[Find(x)] = Find(y);
        }
    }
}
```

### Java

```java
class Solution {
    public boolean equationsPossible(String[] equations) {
        UnionFind uf = new UnionFind(26);

        // Process all equality equations
        for (String equation : equations) {
            if (equation.charAt(1) == '=') {
                int x = equation.charAt(0) - 'a';
                int y = equation.charAt(3) - 'a';
                uf.union(x, y);
            }
        }

        // Check inequality equations
        for (String equation : equations) {
            if (equation.charAt(1) == '!') {
                int x = equation.charAt(0) - 'a';
                int y = equation.charAt(3) - 'a';
                if (uf.find(x) == uf.find(y)) {
                    return false;
                }
            }
        }

        return true;
    }

    private class UnionFind {
        private int[] parent;

        public UnionFind(int n) {
            parent = new int[n];
            for (int i = 0; i < n; i++) {
                parent[i] = i;
            }
        }

        public int find(int x) {
            if (parent[x] != x) {
                parent[x] = find(parent[x]);
            }
            return parent[x];
        }

        public void union(int x, int y) {
            parent[find(x)] = find(y);
        }
    }
}
```

### Swift

```swift
class Solution {
    func equationsPossible(_ equations: [String]) -> Bool {
        let uf = UnionFind(26)

        // Process all equality equations
        for equation in equations where equation.contains("==") {
            let x = Int(equation.first!.asciiValue! - Character("a").asciiValue!)
            let y = Int(equation.last!.asciiValue! - Character("a").asciiValue!)
            uf.union(x, y)
        }

        // Check inequality equations
        for equation in equations where equation.contains("!=") {
            let x = Int(equation.first!.asciiValue! - Character("a").asciiValue!)
            let y = Int(equation.last!.asciiValue! - Character("a").asciiValue!)
            if uf.find(x) == uf.find(y) {
                return false
            }
        }

        return true
    }

    private class UnionFind {
        private var parent: [Int]

        init(_ n: Int) {
            parent = Array(0..<n)
        }

        func find(_ x: Int) -> Int {
            if parent[x] != x {
                parent[x] = find(parent[x])
            }
            return parent[x]
        }

        func union(_ x: Int, _ y: Int) {
            parent[find(x)] = find(y)
        }
    }
}
```

### The End