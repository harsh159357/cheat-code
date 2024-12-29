# Baseball Game

## Problem Statement

You are keeping the scores for a baseball game with the following operations:

- An integer `x` — Record a new score of `x`.
- `"+"` — Record a new score that is the sum of the previous two scores.
- `"D"` — Record a new score that is double the previous score.
- `"C"` — Invalidate the previous score, removing it from the record.

Given a list of strings `ops`, where `ops[i]` is the `i`-th operation, return the total score after all operations are applied.

## Input

```text
ops = ["5", "2", "C", "D", "+"]
```

## Output

```text
30
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun calPoints(ops: Array<String>): Int {
        val stack = Stack<Int>()

        for (op in ops) {
            when (op) {
                "+" -> {
                    val top = stack.pop()
                    val newTop = top + stack.peek()
                    stack.push(top)
                    stack.push(newTop)
                }
                "D" -> stack.push(2 * stack.peek())
                "C" -> stack.pop()
                else -> stack.push(op.toInt())
            }
        }

        return stack.sum()
    }
}

fun main() {
    val ops = arrayOf("5", "2", "C", "D", "+")
    val solution = Solution()
    println("Total score: ${solution.calPoints(ops)}") // Output: 30
}
```


### Dart

```dart
int calPoints(List<String> ops) {
  List<int> stack = [];

  for (String op in ops) {
    if (op == "+") {
      int top = stack.removeLast();
      int newTop = top + stack.last;
      stack.add(top);
      stack.add(newTop);
    } else if (op == "D") {
      stack.add(2 * stack.last);
    } else if (op == "C") {
      stack.removeLast();
    } else {
      stack.add(int.parse(op));
    }
  }

  return stack.fold(0, (sum, score) => sum + score);
}

void main() {
  List<String> ops = ["5", "2", "C", "D", "+"];
  print("Total score: ${calPoints(ops)}"); // Output: 30
}
```


### C#

```csharp
public class Solution {
    public int CalPoints(string[] ops) {
        var stack = new Stack<int>();

        foreach (var op in ops) {
            if (op == "+") {
                int top = stack.Pop();
                int newTop = top + stack.Peek();
                stack.Push(top);
                stack.Push(newTop);
            } else if (op == "D") {
                stack.Push(2 * stack.Peek());
            } else if (op == "C") {
                stack.Pop();
            } else {
                stack.Push(int.Parse(op));
            }
        }

        return stack.Sum();
    }
}
```


### Java

```java
import java.util.Stack;

class Solution {
    public int calPoints(String[] ops) {
        Stack<Integer> stack = new Stack<>();

        for (String op : ops) {
            switch (op) {
                case "+":
                    int top = stack.pop();
                    int newTop = top + stack.peek();
                    stack.push(top);
                    stack.push(newTop);
                    break;
                case "D":
                    stack.push(2 * stack.peek());
                    break;
                case "C":
                    stack.pop();
                    break;
                default:
                    stack.push(Integer.parseInt(op));
                    break;
            }
        }

        int sum = 0;
        for (int score : stack) {
            sum += score;
        }

        return sum;
    }
}
```


### Swift

```swift
class Solution {
    func calPoints(_ ops: [String]) -> Int {
        var stack = [Int]()

        for op in ops {
            switch op {
            case "+":
                let top = stack.removeLast()
                let newTop = top + stack.last!
                stack.append(top)
                stack.append(newTop)
            case "D":
                stack.append(2 * stack.last!)
            case "C":
                stack.removeLast()
            default:
                stack.append(Int(op)!)
            }
        }

        return stack.reduce(0, +)
    }
}

// Example usage
let ops = ["5", "2", "C", "D", "+"]
let solution = Solution()
print("Total score: \(solution.calPoints(ops))") // Output: 30
```

### The End