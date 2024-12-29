# Construct Quad Tree

## Problem Statement

Given a `n x n` binary matrix `grid` where `n` is a power of 2, construct a Quad-Tree and return the root node.  
A Quad-Tree is a tree data structure where each internal node has exactly four children: topLeft, topRight, bottomLeft, bottomRight.  
The Quad-Tree representation for a matrix is based on these rules:
- If all the values in the sub-grid are the same, the node is a leaf with `isLeaf = true` and `val = grid[i][j]`.
- Otherwise, divide the grid into four sub-grids, create four children for the node, and recursively construct the tree.

---

## Input

```text
grid = [[0,1],[1,0]]
```

## Output

```text
Node{val=false, isLeaf=false, 
    topLeft=Node{val=false, isLeaf=true}, 
    topRight=Node{val=true, isLeaf=true}, 
    bottomLeft=Node{val=true, isLeaf=true}, 
    bottomRight=Node{val=false, isLeaf=true}
}
```


## Solutions

### Kotlin

```kotlin
class Node(var `val`: Boolean, var isLeaf: Boolean) {
    var topLeft: Node? = null
    var topRight: Node? = null
    var bottomLeft: Node? = null
    var bottomRight: Node? = null
}

class Solution {
    fun construct(grid: Array<IntArray>): Node? {
        return construct(grid, 0, 0, grid.size)
    }

    private fun construct(grid: Array<IntArray>, r: Int, c: Int, len: Int): Node {
        if (len == 1) return Node(grid[r][c] == 1, true)

        val nextLen = len / 2
        val tl = construct(grid, r, c, nextLen)
        val tr = construct(grid, r, c + nextLen, nextLen)
        val bl = construct(grid, r + nextLen, c, nextLen)
        val br = construct(grid, r + nextLen, c + nextLen, nextLen)

        if (tl.isLeaf && tr.isLeaf && bl.isLeaf && br.isLeaf &&
            tl.`val` == tr.`val` && tr.`val` == bl.`val` && bl.`val` == br.`val`) {
            return Node(tl.`val`, true)
        }

        val root = Node(false, false)
        root.topLeft = tl
        root.topRight = tr
        root.bottomLeft = bl
        root.bottomRight = br
        return root
    }
}
```

### Dart

```dart
class Node {
  bool val;
  bool isLeaf;
  Node? topLeft;
  Node? topRight;
  Node? bottomLeft;
  Node? bottomRight;

  Node(this.val, this.isLeaf, {this.topLeft, this.topRight, this.bottomLeft, this.bottomRight});
}

Node? construct(List<List<int>> grid) {
  return _construct(grid, 0, 0, grid.length);
}

Node _construct(List<List<int>> grid, int r, int c, int len) {
  if (len == 1) return Node(grid[r][c] == 1, true);

  int nextLen = len ~/ 2;
  Node tl = _construct(grid, r, c, nextLen);
  Node tr = _construct(grid, r, c + nextLen, nextLen);
  Node bl = _construct(grid, r + nextLen, c, nextLen);
  Node br = _construct(grid, r + nextLen, c + nextLen, nextLen);

  if (tl.isLeaf &&
      tr.isLeaf &&
      bl.isLeaf &&
      br.isLeaf &&
      tl.val == tr.val &&
      tr.val == bl.val &&
      bl.val == br.val) {
    return Node(tl.val, true);
  }

  return Node(false, false, topLeft: tl, topRight: tr, bottomLeft: bl, bottomRight: br);
}
```

### C#

```csharp
public class Node {
    public bool val;
    public bool isLeaf;
    public Node topLeft;
    public Node topRight;
    public Node bottomLeft;
    public Node bottomRight;

    public Node(bool val, bool isLeaf) {
        this.val = val;
        this.isLeaf = isLeaf;
    }
}

public class Solution {
    public Node Construct(int[][] grid) {
        return Construct(grid, 0, 0, grid.Length);
    }

    private Node Construct(int[][] grid, int r, int c, int len) {
        if (len == 1) return new Node(grid[r][c] == 1, true);

        int nextLen = len / 2;
        Node tl = Construct(grid, r, c, nextLen);
        Node tr = Construct(grid, r, c + nextLen, nextLen);
        Node bl = Construct(grid, r + nextLen, c, nextLen);
        Node br = Construct(grid, r + nextLen, c + nextLen, nextLen);

        if (tl.isLeaf && tr.isLeaf && bl.isLeaf && br.isLeaf &&
            tl.val == tr.val && tr.val == bl.val && bl.val == br.val) {
            return new Node(tl.val, true);
        }

        Node root = new Node(false, false) {
            topLeft = tl,
            topRight = tr,
            bottomLeft = bl,
            bottomRight = br
        };
        return root;
    }
}
```

### Java

```java
class Node {
    public boolean val;
    public boolean isLeaf;
    public Node topLeft;
    public Node topRight;
    public Node bottomLeft;
    public Node bottomRight;

    public Node(boolean val, boolean isLeaf) {
        this.val = val;
        this.isLeaf = isLeaf;
    }
}

class Solution {
    public Node construct(int[][] grid) {
        return construct(grid, 0, 0, grid.length);
    }

    private Node construct(int[][] grid, int r, int c, int len) {
        if (len == 1) return new Node(grid[r][c] == 1, true);

        int nextLen = len / 2;
        Node tl = construct(grid, r, c, nextLen);
        Node tr = construct(grid, r, c + nextLen, nextLen);
        Node bl = construct(grid, r + nextLen, c, nextLen);
        Node br = construct(grid, r + nextLen, c + nextLen, nextLen);

        if (tl.isLeaf && tr.isLeaf && bl.isLeaf && br.isLeaf &&
            tl.val == tr.val && tr.val == bl.val && bl.val == br.val) {
            return new Node(tl.val, true);
        }

        Node root = new Node(false, false);
        root.topLeft = tl;
        root.topRight = tr;
        root.bottomLeft = bl;
        root.bottomRight = br;
        return root;
    }
}
```


### Swift

```swift
class Node {
    var val: Bool
    var isLeaf: Bool
    var topLeft: Node?
    var topRight: Node?
    var bottomLeft: Node?
    var bottomRight: Node?

    init(_ val: Bool, _ isLeaf: Bool) {
        self.val = val
        self.isLeaf = isLeaf
    }
}

class Solution {
    func construct(_ grid: [[Int]]) -> Node? {
        return construct(grid, 0, 0, grid.count)
    }

    private func construct(_ grid: [[Int]], _ r: Int, _ c: Int, _ len: Int) -> Node {
        if len == 1 {
            return Node(grid[r][c] == 1, true)
        }

        let nextLen = len / 2
        let tl = construct(grid, r, c, nextLen)
        let tr = construct(grid, r, c + nextLen, nextLen)
        let bl = construct(grid, r + nextLen, c, nextLen)
        let br = construct(grid, r + nextLen, c + nextLen, nextLen)

        if tl.isLeaf && tr.isLeaf && bl.isLeaf && br.isLeaf &&
            tl.val == tr.val && tr.val == bl.val && bl.val == br.val {
            return Node(tl.val, true)
        }

        let root = Node(false, false)
        root.topLeft = tl
        root.topRight = tr
        root.bottomLeft = bl
        root.bottomRight = br
        return root
    }
}
```


### The End