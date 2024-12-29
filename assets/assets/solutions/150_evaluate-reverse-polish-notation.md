# Evaluate Reverse Polish Notation

## Problem Statement

Evaluate the value of an arithmetic expression in Reverse Polish Notation (RPN).

Valid operators are `+`, `-`, `*`, and `/`. Each operand may be an integer or another expression. Division between two integers should truncate toward zero.

---

## Input

```text
tokens = ["2", "1", "+", "3", "*"]
```

---

## Output

```text
9
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun evalRPN(tokens: Array<String>): Int {
        val stack = Stack<Int>()
        for (token in tokens) {
            when (token) {
                "+", "-", "*", "/" -> {
                    val b = stack.pop()
                    val a = stack.pop()
                    val result = when (token) {
                        "+" -> a + b
                        "-" -> a - b
                        "*" -> a * b
                        "/" -> a / b
                        else -> throw IllegalArgumentException("Invalid operator")
                    }
                    stack.push(result)
                }
                else -> stack.push(token.toInt())
            }
        }
        return stack.pop()
    }
}
```


### Dart

```dart
int evalRPN(List<String> tokens) {
  final stack = <int>[];

  for (var token in tokens) {
    if (['+', '-', '*', '/'].contains(token)) {
      final b = stack.removeLast();
      final a = stack.removeLast();
      switch (token) {
        case '+':
          stack.add(a + b);
          break;
        case '-':
          stack.add(a - b);
          break;
        case '*':
          stack.add(a * b);
          break;
        case '/':
          stack.add(a ~/ b); // Truncated integer division
          break;
      }
    } else {
      stack.add(int.parse(token));
    }
  }

  return stack.last;
}
```


### C#

```csharp
public class Solution {
    public int EvalRPN(string[] tokens) {
        Stack<int> stack = new Stack<int>();

        foreach (string token in tokens) {
            if (token == "+" || token == "-" || token == "*" || token == "/") {
                int b = stack.Pop();
                int a = stack.Pop();
                int result = token switch {
                    "+" => a + b,
                    "-" => a - b,
                    "*" => a * b,
                    "/" => a / b,
                    _ => throw new ArgumentException("Invalid operator")
                };
                stack.Push(result);
            } else {
                stack.Push(int.Parse(token));
            }
        }

        return stack.Pop();
    }
}
```


### Java

```java
import java.util.Stack;

class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>();
        for (String token : tokens) {
            switch (token) {
                case "+":
                    stack.push(stack.pop() + stack.pop());
                    break;
                case "-":
                    int b = stack.pop();
                    int a = stack.pop();
                    stack.push(a - b);
                    break;
                case "*":
                    stack.push(stack.pop() * stack.pop());
                    break;
                case "/":
                    b = stack.pop();
                    a = stack.pop();
                    stack.push(a / b);
                    break;
                default:
                    stack.push(Integer.parseInt(token));
            }
        }
        return stack.pop();
    }
}
```


### Swift

```swift
class Solution {
    func evalRPN(_ tokens: [String]) -> Int {
        var stack = [Int]()

        for token in tokens {
            switch token {
            case "+":
                let b = stack.removeLast()
                let a = stack.removeLast()
                stack.append(a + b)
            case "-":
                let b = stack.removeLast()
                let a = stack.removeLast()
                stack.append(a - b)
            case "*":
                let b = stack.removeLast()
                let a = stack.removeLast()
                stack.append(a * b)
            case "/":
                let b = stack.removeLast()
                let a = stack.removeLast()
                stack.append(a / b)
            default:
                stack.append(Int(token)!)
            }
        }

        return stack.last!
    }
}
```



### The End

