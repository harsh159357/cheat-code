# Min Stack

## Problem Statement

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the `MinStack` class:
- `MinStack()` initializes the stack object.
- `void push(int val)` pushes the element `val` onto the stack.
- `void pop()` removes the element on the top of the stack.
- `int top()` retrieves the top element of the stack.
- `int getMin()` retrieves the minimum element in the stack.

You must implement a solution with `O(1)` time complexity for each function.

---

## Example Input

```text
["MinStack", "push", "push", "push", "getMin", "pop", "top", "getMin"]
[[], [-2], [0], [-3], [], [], [], []]
```

---

## Example Output

```text
[null, null, null, null, -3, null, 0, -2]
```


## Solutions

### Kotlin

```kotlin
class MinStack() {
    private val stack = Stack<Int>()
    private val minStack = Stack<Int>()

    fun push(x: Int) {
        stack.push(x)
        if (minStack.isEmpty() || x <= minStack.peek()) {
            minStack.push(x)
        }
    }

    fun pop() {
        if (stack.pop() == minStack.peek()) {
            minStack.pop()
        }
    }

    fun top(): Int {
        return stack.peek()
    }

    fun getMin(): Int {
        return minStack.peek()
    }
}
```


### Dart

```dart
class MinStack {
  final List<int> stack = [];
  final List<int> minStack = [];

  void push(int x) {
    stack.add(x);
    if (minStack.isEmpty || x <= minStack.last) {
      minStack.add(x);
    }
  }

  void pop() {
    if (stack.removeLast() == minStack.last) {
      minStack.removeLast();
    }
  }

  int top() {
    return stack.last;
  }

  int getMin() {
    return minStack.last;
  }
}
```


### C#

```csharp
public class MinStack {
    private Stack<int> stack = new Stack<int>();
    private Stack<int> minStack = new Stack<int>();

    public void Push(int x) {
        stack.Push(x);
        if (minStack.Count == 0 || x <= minStack.Peek()) {
            minStack.Push(x);
        }
    }

    public void Pop() {
        if (stack.Pop() == minStack.Peek()) {
            minStack.Pop();
        }
    }

    public int Top() {
        return stack.Peek();
    }

    public int GetMin() {
        return minStack.Peek();
    }
}
```


### Java

```java
class MinStack {
    private Stack<Integer> stack;
    private Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack<>();
        minStack = new Stack<>();
    }

    public void push(int val) {
        stack.push(val);
        if (minStack.isEmpty() || val <= minStack.peek()) {
            minStack.push(val);
        }
    }

    public void pop() {
        if (stack.pop().equals(minStack.peek())) {
            minStack.pop();
        }
    }

    public int top() {
        return stack.peek();
    }

    public int getMin() {
        return minStack.peek();
    }
}
```


### Swift

```swift
class MinStack {
    private var stack: [Int] = []
    private var minStack: [Int] = []

    func push(_ val: Int) {
        stack.append(val)
        if minStack.isEmpty || val <= minStack.last! {
            minStack.append(val)
        }
    }

    func pop() {
        if stack.removeLast() == minStack.last! {
            minStack.removeLast()
        }
    }

    func top() -> Int {
        return stack.last!
    }

    func getMin() -> Int {
        return minStack.last!
    }
}
```


### The End

