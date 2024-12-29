# Kth Smallest Element in a BST

## Problem Statement

Given the `root` of a binary search tree and an integer `k`, return the `k`th smallest value (1-indexed) of all the values of the nodes in the tree.

## Input

```text
root = [3, 1, 4, null, 2], k = 1
```

## Output

```text
1
```

## Solutions

### Dart

```dart
class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;
  TreeNode(this.val, [this.left, this.right]);
}

int kthSmallest(TreeNode? root, int k) {
  List<TreeNode> stack = [];
  TreeNode? current = root;
  int count = 0;

  while (current != null || stack.isNotEmpty) {
    while (current != null) {
      stack.add(current);
      current = current.left;
    }
    current = stack.removeLast();
    count++;
    if (count == k) {
      return current.val;
    }
    current = current.right;
  }
  throw Exception("k is out of range");
}
```

### C#

```csharp
public class TreeNode {
    public int val;
    public TreeNode left;
    public TreeNode right;
    public TreeNode(int x) { val = x; }
}

public class Solution {
    public int KthSmallest(TreeNode root, int k) {
        Stack<TreeNode> stack = new Stack<TreeNode>();
        TreeNode current = root;
        int count = 0;

        while (current != null || stack.Count > 0) {
            while (current != null) {
                stack.Push(current);
                current = current.left;
            }
            current = stack.Pop();
            count++;
            if (count == k) {
                return current.val;
            }
            current = current.right;
        }
        throw new Exception("k is out of range");
    }
}
```

### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {
    public int kthSmallest(TreeNode root, int k) {
        Stack<TreeNode> stack = new Stack<>();
        TreeNode current = root;
        int count = 0;

        while (current != null || !stack.isEmpty()) {
            while (current != null) {
                stack.push(current);
                current = current.left;
            }
            current = stack.pop();
            count++;
            if (count == k) {
                return current.val;
            }
            current = current.right;
        }
        throw new IllegalArgumentException("k is out of range");
    }
}
```

### Kotlin

```kotlin
class TreeNode(var `val`: Int) {
    var left: TreeNode? = null
    var right: TreeNode? = null
}

class Solution {
    fun kthSmallest(root: TreeNode?, k: Int): Int {
        val stack = mutableListOf<TreeNode>()
        var curr = root
        var count = 0
        var result = 0

        while (curr != null || stack.isNotEmpty()) {
            while (curr != null) {
                stack.add(curr)
                curr = curr.left
            }
            curr = stack.removeAt(stack.size - 1)
            count++
            if (count == k) {
                result = curr.`val`
                break
            }
            curr = curr.right
        }
        return result
    }
}
```

### Swift

```swift
public class TreeNode {
    public var val: Int
    public var left: TreeNode?
    public var right: TreeNode?
    public init() { self.val = 0; self.left = nil; self.right = nil; }
    public init(_ val: Int) { self.val = val; self.left = nil; self.right = nil; }
    public init(_ val: Int, _ left: TreeNode?, _ right: TreeNode?) {
        self.val = val
        self.left = left
        self.right = right
    }
}

class Solution {
    func kthSmallest(_ root: TreeNode?, _ k: Int) -> Int {
        var stack = [TreeNode]()
        var current = root
        var count = 0

        while current != nil || !stack.isEmpty {
            while current != nil {
                stack.append(current!)
                current = current?.left
            }
            current = stack.removeLast()
            count += 1
            if count == k {
                return current!.val
            }
            current = current?.right
        }
        fatalError("k is out of range")
    }
}
```

### The End

