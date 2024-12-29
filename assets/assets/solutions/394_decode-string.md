# Decode String

## Problem Statement

Given an encoded string, return its decoded string.

The encoding rule is: `k[encoded_string]`, where the `encoded_string` inside the square brackets is repeated exactly `k` times. You may assume that the input string is always valid and does not contain extra spaces.

## Input

```text
s = "3[a2[c]]"
```

## Output

```text
accaccacc
```

## Solutions

### Dart

```dart
String decodeString(String s) {
  List<int> repeatStack = [];
  List<StringBuffer> resultStack = [StringBuffer()];
  int numOfRepeats = 0;

  for (var ch in s.runes) {
    if (ch >= 48 && ch <= 57) { // '0'..'9'
      numOfRepeats = numOfRepeats * 10 + (ch - 48);
    } else if (ch == 91) { // '['
      repeatStack.add(numOfRepeats);
      resultStack.add(StringBuffer());
      numOfRepeats = 0;
    } else if (ch == 93) { // ']'
      StringBuffer current = resultStack.removeLast();
      int repeats = repeatStack.removeLast();
      resultStack.last.write(current.toString() * repeats);
    } else {
      resultStack.last.write(String.fromCharCode(ch));
    }
  }

  return resultStack.first.toString();
}
```

### C#

```csharp
public class Solution {
    public string DecodeString(string s) {
        Stack<int> repeatStack = new Stack<int>();
        Stack<string> resultStack = new Stack<string>();
        StringBuilder current = new StringBuilder();
        int numOfRepeats = 0;

        foreach (char ch in s) {
            if (char.IsDigit(ch)) {
                numOfRepeats = numOfRepeats * 10 + (ch - '0');
            } else if (ch == '[') {
                repeatStack.Push(numOfRepeats);
                resultStack.Push(current.ToString());
                current.Clear();
                numOfRepeats = 0;
            } else if (ch == ']') {
                string temp = current.ToString();
                current.Clear();
                current.Append(resultStack.Pop());
                int repeats = repeatStack.Pop();
                for (int i = 0; i < repeats; i++) {
                    current.Append(temp);
                }
            } else {
                current.Append(ch);
            }
        }

        return current.ToString();
    }
}
```

### Java

```java
import java.util.Stack;

class Solution {
    public String decodeString(String s) {
        Stack<Integer> repeatStack = new Stack<>();
        Stack<StringBuilder> resultStack = new Stack<>();
        StringBuilder current = new StringBuilder();
        int numOfRepeats = 0;

        for (char ch : s.toCharArray()) {
            if (Character.isDigit(ch)) {
                numOfRepeats = numOfRepeats * 10 + (ch - '0');
            } else if (ch == '[') {
                repeatStack.push(numOfRepeats);
                resultStack.push(current);
                current = new StringBuilder();
                numOfRepeats = 0;
            } else if (ch == ']') {
                StringBuilder temp = current;
                current = resultStack.pop();
                int repeats = repeatStack.pop();
                for (int i = 0; i < repeats; i++) {
                    current.append(temp);
                }
            } else {
                current.append(ch);
            }
        }

        return current.toString();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun decodeString(s: String): String = buildString {
        val repeatStack = ArrayDeque<IntArray>()
        var numOfRepeats = 0
        for (ch in s) {
            when (ch) {
                in '0'..'9' -> numOfRepeats = numOfRepeats * 10 + (ch - '0')
                '[' -> {
                    repeatStack += intArrayOf(numOfRepeats, length)
                    numOfRepeats = 0
                }
                ']' -> {
                    val (repeats, startIdx) = repeatStack.removeLast()
                    if (repeats > 1) {
                        val substring = this.substring(startIdx)
                        repeat(repeats - 1) { append(substring) }
                    }
                }
                else -> append(ch)
            }
        }
    }
}
```

### Swift

```swift
class Solution {
    func decodeString(_ s: String) -> String {
        var repeatStack = [Int]()
        var resultStack = [String]()
        var current = ""
        var numOfRepeats = 0

        for ch in s {
            if ch.isNumber {
                numOfRepeats = numOfRepeats * 10 + Int(String(ch))!
            } else if ch == "[" {
                repeatStack.append(numOfRepeats)
                resultStack.append(current)
                current = ""
                numOfRepeats = 0
            } else if ch == "]" {
                let repeats = repeatStack.removeLast()
                let temp = current
                current = resultStack.removeLast()
                for _ in 0..<repeats {
                    current.append(temp)
                }
            } else {
                current.append(ch)
            }
        }

        return current
    }
}
```

### The End