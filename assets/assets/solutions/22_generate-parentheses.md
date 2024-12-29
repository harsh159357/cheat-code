# Generate Parentheses

## Problem Statement

Given `n` pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

## Input

```text
n = 3
```

## Output

```text
["((()))", "(()())", "(())()", "()(())", "()()()"]
```

## Solutions

### Dart

```dart
List<String> generateParenthesis(int n) {
  List<String> result = [];

  void backtrack(String str, int open, int close, int max) {
    if (str.length == max * 2) {
      result.add(str);
      return;
    }

    if (open < max) {
      backtrack(str + "(", open + 1, close, max);
    }

    if (close < open) {
      backtrack(str + ")", open, close + 1, max);
    }
  }

  backtrack("", 0, 0, n);
  return result;
}

void main() {
  print(generateParenthesis(3)); // Output: ["((()))", "(()())", "(())()", "()(())", "()()()"]
}
```

### C#

```csharp
public class Solution {
    public IList<string> GenerateParenthesis(int n) {
        var result = new List<string>();

        void Backtrack(string str, int open, int close, int max) {
            if (str.Length == max * 2) {
                result.Add(str);
                return;
            }

            if (open < max) {
                Backtrack(str + "(", open + 1, close, max);
            }

            if (close < open) {
                Backtrack(str + ")", open, close + 1, max);
            }
        }

        Backtrack("", 0, 0, n);
        return result;
    }
}
```

### Java

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();

        void backtrack(String str, int open, int close, int max) {
            if (str.length() == max * 2) {
                result.add(str);
                return;
            }

            if (open < max) {
                backtrack(str + "(", open + 1, close, max);
            }

            if (close < open) {
                backtrack(str + ")", open, close + 1, max);
            }
        }

        backtrack("", 0, 0, n);
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun generateParenthesis(n: Int): List<String> {
        val result = mutableListOf<String>()
        backtrack("", 0, 0, n, result)
        return result
    }

    private fun backtrack(
        str: String,
        open: Int,
        close: Int,
        max: Int,
        result: MutableList<String>
    ) {
        if (str.length == max * 2) {
            result.add(str)
            return
        }

        if (open < max) backtrack("$str(", open + 1, close, max, result)
        if (close < open) backtrack("$str)", open, close + 1, max, result)
    }
}
```

### Swift

```swift
class Solution {
    func generateParenthesis(_ n: Int) -> [String] {
        var result: [String] = []

        func backtrack(_ str: String, _ open: Int, _ close: Int, _ max: Int) {
            if str.count == max * 2 {
                result.append(str)
                return
            }

            if open < max {
                backtrack(str + "(", open + 1, close, max)
            }

            if close < open {
                backtrack(str + ")", open, close + 1, max)
            }
        }

        backtrack("", 0, 0, n)
        return result
    }
}

let solution = Solution()
print(solution.generateParenthesis(3)) // Output: ["((()))", "(()())", "(())()", "()(())", "()()()"]
```


### The End

