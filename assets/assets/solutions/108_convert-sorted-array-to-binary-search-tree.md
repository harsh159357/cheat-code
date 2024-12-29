# Convert Sorted Array to Binary Search Tree

## Problem Statement

Given an integer array `nums` where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

## Input

```text
nums = [-10, -3, 0, 5, 9]
```

## Output

```text
TreeNode representing the binary search tree:
       0
      / \
   -10   5
     \    \
     -3    9
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

TreeNode? sortedArrayToBST(List<int> nums) {
  return buildBST(nums, 0, nums.length - 1);
}

TreeNode? buildBST(List<int> nums, int start, int end) {
  if (start > end) return null;
  int mid = (start + end) ~/ 2;
  TreeNode root = TreeNode(nums[mid]);
  root.left = buildBST(nums, start, mid - 1);
  root.right = buildBST(nums, mid + 1, end);
  return root;
}
```


### C#

```csharp
public class TreeNode {
    public int val;
    public TreeNode left;
    public TreeNode right;
    public TreeNode(int val = 0, TreeNode left = null, TreeNode right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

public class Solution {
    public TreeNode SortedArrayToBST(int[] nums) {
        return BuildBST(nums, 0, nums.Length - 1);
    }

    private TreeNode BuildBST(int[] nums, int start, int end) {
        if (start > end) return null;
        int mid = (start + end) / 2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = BuildBST(nums, start, mid - 1);
        root.right = BuildBST(nums, mid + 1, end);
        return root;
    }
}
```


### Java

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode() {}
    TreeNode(int val) { this.val = val; }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        return buildBST(nums, 0, nums.length - 1);
    }

    private TreeNode buildBST(int[] nums, int start, int end) {
        if (start > end) return null;
        int mid = (start + end) / 2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = buildBST(nums, start, mid - 1);
        root.right = buildBST(nums, mid + 1, end);
        return root;
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
    fun sortedArrayToBST(nums: IntArray): TreeNode? {
        return sortedArrayToBST(nums, 0, nums.lastIndex)
    }

    private fun sortedArrayToBST(nums: IntArray, start: Int, end: Int): TreeNode? {
        return if (start > end) null
        else {
            val mid = (start + end) / 2
            TreeNode(nums[mid]).apply {
                left = sortedArrayToBST(nums, start, mid - 1)
                right = sortedArrayToBST(nums, mid + 1, end)
            }
        }
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
    func sortedArrayToBST(_ nums: [Int]) -> TreeNode? {
        return buildBST(nums, 0, nums.count - 1)
    }

    private func buildBST(_ nums: [Int], _ start: Int, _ end: Int) -> TreeNode? {
        if start > end { return nil }
        let mid = (start + end) / 2
        let root = TreeNode(nums[mid])
        root.left = buildBST(nums, start, mid - 1)
        root.right = buildBST(nums, mid + 1, end)
        return root
    }
}
```


### The End

