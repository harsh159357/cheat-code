# Basic Calculator

## Problem Statement

Given a string `s` representing a valid mathematical expression, implement a basic calculator to evaluate it.

The expression string may contain:
- Non-negative integers
- `'+'`, `'-'`, `'('`, `')'` operators
- Empty spaces `' '`.

## Input

```text
s = "(1+(4+5+2)-3)+(6+8)"
```

## Output

```text
23
```

## Solutions

### Dart

```dart
int calculate(String s) {
  List<int> stack = [];
  int result = 0, num = 0, sign = 1;

  for (int i = 0; i < s.length; i++) {
    String c = s[i];
    if (c == '+') {
      result += sign * num;
      num = 0;
      sign = 1;
    } else if (c == '-') {
      result += sign * num;
      num = 0;
      sign = -1;
    } else if (c == '(') {
      stack.add(result);
      stack.add(sign);
      result = 0;
      sign = 1;
    } else if (c == ')') {
      result += sign * num;
      num = 0;
      result *= stack.removeLast();
      result += stack.removeLast();
    } else if (c.codeUnitAt(0) >= '0'.codeUnitAt(0) && c.codeUnitAt(0) <= '9'.codeUnitAt(0)) {
      num = num * 10 + (c.codeUnitAt(0) - '0'.codeUnitAt(0));
    }
  }
  return result + sign * num;
}
```

### C#

```csharp
public class Solution {
    public int Calculate(string s) {
        Stack<int> stack = new Stack<int>();
        int result = 0, num = 0, sign = 1;

        foreach (char c in s) {
            if (char.IsDigit(c)) {
                num = num * 10 + (c - '0');
            } else if (c == '+') {
                result += sign * num;
                num = 0;
                sign = 1;
            } else if (c == '-') {
                result += sign * num;
                num = 0;
                sign = -1;
            } else if (c == '(') {
                stack.Push(result);
                stack.Push(sign);
                result = 0;
                sign = 1;
            } else if (c == ')') {
                result += sign * num;
                num = 0;
                result *= stack.Pop();
                result += stack.Pop();
            }
        }
        return result + sign * num;
    }
}
```

### Java

```java
class Solution {
    public int calculate(String s) {
        Stack<Integer> stack = new Stack<>();
        int result = 0, num = 0, sign = 1;

        for (char c : s.toCharArray()) {
            if (Character.isDigit(c)) {
                num = num * 10 + (c - '0');
            } else if (c == '+') {
                result += sign * num;
                num = 0;
                sign = 1;
            } else if (c == '-') {
                result += sign * num;
                num = 0;
                sign = -1;
            } else if (c == '(') {
                stack.push(result);
                stack.push(sign);
                result = 0;
                sign = 1;
            } else if (c == ')') {
                result += sign * num;
                num = 0;
                result *= stack.pop();
                result += stack.pop();
            }
        }
        return result + sign * num;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun calculate(s: String): Int {
        val stack = Stack<Int>()
        var result = 0
        var num = 0
        var sign = 1
        for (c in s) {
            when (c) {
                '+' -> {
                    result += sign * num
                    num = 0
                    sign = 1
                }
                '-' -> {
                    result += sign * num
                    num = 0
                    sign = -1
                }
                '(' -> {
                    stack.push(result)
                    stack.push(sign)
                    result = 0
                    sign = 1
                }
                ')' -> {
                    result += sign * num
                    num = 0
                    result *= stack.pop()
                    result += stack.pop()
                }
                in '0'..'9' -> {
                    num = num * 10 + (c - '0')
                }
            }
        }
        return result + sign * num
    }
}
```

### Swift

```swift
class Solution {
    func calculate(_ s: String) -> Int {
        var stack = [Int]()
        var result = 0
        var num = 0
        var sign = 1

        for char in s {
            switch char {
            case "+":
                result += sign * num
                num = 0
                sign = 1
            case "-":
                result += sign * num
                num = 0
                sign = -1
            case "(":
                stack.append(result)
                stack.append(sign)
                result = 0
                sign = 1
            case ")":
                result += sign * num
                num = 0
                result *= stack.removeLast()
                result += stack.removeLast()
            case "0"..."9":
                num = num * 10 + Int(String(char))!
            default:
                continue
            }
        }
        return result + sign * num
    }
}
```


### The End

