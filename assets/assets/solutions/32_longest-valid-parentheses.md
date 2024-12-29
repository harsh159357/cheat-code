# Longest Valid Parentheses

## Problem Statement

Given a string containing just the characters `(` and `)`, find the length of the longest valid (well-formed) parentheses substring.

## Input

```text
s = "(()"
```

## Output

```text
2  
(Explanation: The longest valid parentheses substring is "()".)
```

## Solutions

### Dart

```dart
int longestValidParentheses(String s) {
  int maxLen = 0;
  List<int> dp = List.filled(s.length, 0);

  for (int i = 1; i < s.length; i++) {
    if (s[i] == ')') {
      if (s[i - 1] == '(') {
        dp[i] = (i >= 2 ? dp[i - 2] : 0) + 2;
      } else if (i - dp[i - 1] > 0 && s[i - dp[i - 1] - 1] == '(') {
        dp[i] = dp[i - 1] + (i - dp[i - 1] >= 2 ? dp[i - dp[i - 1] - 2] : 0) + 2;
      }
      maxLen = maxLen > dp[i] ? maxLen : dp[i];
    }
  }

  return maxLen;
}

void main() {
  print(longestValidParentheses("(()")); // Output: 2
  print(longestValidParentheses(")()())")); // Output: 4
  print(longestValidParentheses("")); // Output: 0
}
```

### C#

```csharp
public class Solution {
    public int LongestValidParentheses(string s) {
        int maxLen = 0;
        int[] dp = new int[s.Length];

        for (int i = 1; i < s.Length; i++) {
            if (s[i] == ')') {
                if (s[i - 1] == '(') {
                    dp[i] = (i >= 2 ? dp[i - 2] : 0) + 2;
                } else if (i - dp[i - 1] > 0 && s[i - dp[i - 1] - 1] == '(') {
                    dp[i] = dp[i - 1] + (i - dp[i - 1] >= 2 ? dp[i - dp[i - 1] - 2] : 0) + 2;
                }
                maxLen = Math.Max(maxLen, dp[i]);
            }
        }

        return maxLen;
    }
}
```

### Java

```java
class Solution {
    public int longestValidParentheses(String s) {
        int maxLen = 0;
        int[] dp = new int[s.length()];

        for (int i = 1; i < s.length(); i++) {
            if (s.charAt(i) == ')') {
                if (s.charAt(i - 1) == '(') {
                    dp[i] = (i >= 2 ? dp[i - 2] : 0) + 2;
                } else if (i - dp[i - 1] > 0 && s.charAt(i - dp[i - 1] - 1) == '(') {
                    dp[i] = dp[i - 1] + (i - dp[i - 1] >= 2 ? dp[i - dp[i - 1] - 2] : 0) + 2;
                }
                maxLen = Math.max(maxLen, dp[i]);
            }
        }

        return maxLen;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun longestValidParentheses(s: String): Int {
        var maxLen = 0
        val dp = IntArray(s.length)

        for (i in 1 until s.length) {
            if (s[i] == ')') {
                if (s[i - 1] == '(') {
                    dp[i] = if (i >= 2) dp[i - 2] + 2 else 2
                } else if (i - dp[i - 1] > 0 && s[i - dp[i - 1] - 1] == '(') {
                    dp[i] = dp[i - 1] + (if (i - dp[i - 1] >= 2) dp[i - dp[i - 1] - 2] else 0) + 2
                }
                maxLen = maxOf(maxLen, dp[i])
            }
        }

        return maxLen
    }
}
```

### Swift

```swift
class Solution {
    func longestValidParentheses(_ s: String) -> Int {
        var maxLen = 0
        var dp = [Int](repeating: 0, count: s.count)

        let chars = Array(s)

        for i in 1..<chars.count {
            if chars[i] == ")" {
                if chars[i - 1] == "(" {
                    dp[i] = (i >= 2 ? dp[i - 2] : 0) + 2
                } else if i - dp[i - 1] > 0 && chars[i - dp[i - 1] - 1] == "(" {
                    dp[i] = dp[i - 1] + (i - dp[i - 1] >= 2 ? dp[i - dp[i - 1] - 2] : 0) + 2
                }
                maxLen = max(maxLen, dp[i])
            }
        }

        return maxLen
    }
}

let solution = Solution()
print(solution.longestValidParentheses("(()")) // Output: 2
print(solution.longestValidParentheses(")()())")) // Output: 4
print(solution.longestValidParentheses("")) // Output: 0
```


### The End

