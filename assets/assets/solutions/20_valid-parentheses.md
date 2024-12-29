# Valid Parentheses

## Problem Statement

Given a string `s` containing just the characters `'(', ')', '{', '}', '['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

## Input

```text
s = "()[]{}"
```

## Output

```text
true

(Explanation: All brackets are matched and in correct order.)
```

## Solutions

### Dart

```dart
bool isValid(String s) {
  final stack = <String>[];
  final map = {')': '(', ']': '[', '}': '{'};

  for (var char in s.split('')) {
    if (map.containsKey(char)) {
      if (stack.isEmpty || stack.removeLast() != map[char]) {
        return false;
      }
    } else {
      stack.add(char);
    }
  }

  return stack.isEmpty;
}

void main() {
  print(isValid("()[]{}")); // Output: true
  print(isValid("(]"));     // Output: false
  print(isValid("([)]"));   // Output: false
}
```

### C#

```csharp
public class Solution {
    public bool IsValid(string s) {
        var stack = new Stack<char>();
        var map = new Dictionary<char, char> {
            {')', '('},
            {']', '['},
            {'}', '{'}
        };

        foreach (var c in s) {
            if (map.ContainsKey(c)) {
                if (stack.Count == 0 || stack.Pop() != map[c]) {
                    return false;
                }
            } else {
                stack.Push(c);
            }
        }

        return stack.Count == 0;
    }
}
```

### Java

```java
import java.util.Stack;

class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        Map<Character, Character> map = Map.of(
            ')', '(',
            ']', '[',
            '}', '{'
        );

        for (char c : s.toCharArray()) {
            if (map.containsKey(c)) {
                if (stack.isEmpty() || stack.pop() != map.get(c)) {
                    return false;
                }
            } else {
                stack.push(c);
            }
        }

        return stack.isEmpty();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isValid(s: String): Boolean {
        val stack = Stack<Char>()
        val map = mapOf(')' to '(', ']' to '[', '}' to '{')

        for (c in s) {
            if (map.containsKey(c)) {
                if (stack.isEmpty() || stack.pop() != map[c]) return false
            } else {
                stack.push(c)
            }
        }

        return stack.isEmpty()
    }
}
```

### Swift

```swift
class Solution {
    func isValid(_ s: String) -> Bool {
        var stack = [Character]()
        let map: [Character: Character] = [
            ')': '(',
            ']': '[',
            '}': '{'
        ]

        for char in s {
            if let match = map[char] {
                if stack.isEmpty || stack.removeLast() != match {
                    return false
                }
            } else {
                stack.append(char)
            }
        }

        return stack.isEmpty
    }
}

let solution = Solution()
print(solution.isValid("()[]{}")) // Output: true
print(solution.isValid("(]"))     // Output: false
print(solution.isValid("([)]"))   // Output: false
```


### The End

