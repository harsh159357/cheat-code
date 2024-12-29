# Decode Ways

## Problem Statement

A message containing letters from `A-Z` can be encoded into numbers using the following mapping:

```text
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

To decode an encoded message, determine the total number of ways it can be decoded.

## Input

```text
s = "226"
```

## Output

```text
3
```

(Explanation: The message can be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).)

## Solutions

### Dart

```dart
int numDecodings(String s) {
  List<int?> memo = List.filled(s.length + 1, null);
  return _numDecodings(s, 0, memo);
}

int _numDecodings(String s, int index, List<int?> memo) {
  if (index == s.length) {
    return 1;
  }
  if (s[index] == '0') {
    return 0;
  }
  if (memo[index] != null) {
    return memo[index]!;
  }
  int way1 = _numDecodings(s, index + 1, memo);
  int way2 = 0;
  if (index < s.length - 1 && int.parse(s.substring(index, index + 2)) <= 26) {
    way2 = _numDecodings(s, index + 2, memo);
  }
  memo[index] = way1 + way2;
  return memo[index]!;
}

void main() {
  print(numDecodings("226")); // Output: 3
}
```

### C#

```csharp
public class Solution {
    public int NumDecodings(string s) {
        int[] memo = new int[s.Length + 1];
        Array.Fill(memo, -1);
        return NumDecodings(s, 0, memo);
    }

    private int NumDecodings(string s, int index, int[] memo) {
        if (index == s.Length) {
            return 1;
        }
        if (s[index] == '0') {
            return 0;
        }
        if (memo[index] != -1) {
            return memo[index];
        }
        int way1 = NumDecodings(s, index + 1, memo);
        int way2 = 0;
        if (index < s.Length - 1 && int.Parse(s.Substring(index, 2)) <= 26) {
            way2 = NumDecodings(s, index + 2, memo);
        }
        memo[index] = way1 + way2;
        return memo[index];
    }
}
```

### Java

```java
class Solution {
    public int numDecodings(String s) {
        Integer[] memo = new Integer[s.length() + 1];
        return numDecodings(s, 0, memo);
    }

    private int numDecodings(String s, int index, Integer[] memo) {
        if (index == s.length()) {
            return 1;
        }
        if (s.charAt(index) == '0') {
            return 0;
        }
        if (memo[index] != null) {
            return memo[index];
        }
        int way1 = numDecodings(s, index + 1, memo);
        int way2 = 0;
        if (index < s.length() - 1 && Integer.parseInt(s.substring(index, index + 2)) <= 26) {
            way2 = numDecodings(s, index + 2, memo);
        }
        memo[index] = way1 + way2;
        return memo[index];
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun numDecodings(s: String): Int {
        val memo = arrayOfNulls<Int>(s.length + 1)
        return numDecodings(s, 0, memo)
    }

    private fun numDecodings(s: String, index: Int, memo: Array<Int?>): Int {
        if (index == s.length) {
            return 1
        }
        if (s[index] == '0') {
            return 0
        }
        if (memo[index] != null) {
            return memo[index]!!
        }
        val way1 = numDecodings(s, index + 1, memo)
        var way2 = 0
        if (index < s.length - 1 && s.substring(index, index + 2).toInt() <= 26) {
            way2 = numDecodings(s, index + 2, memo)
        }
        memo[index] = way1 + way2
        return memo[index]!!
    }
}

fun main() {
    val solution = Solution()
    println(solution.numDecodings("226")) // Output: 3
}
```

### Swift

```swift
class Solution {
    func numDecodings(_ s: String) -> Int {
        var memo = [Int?](repeating: nil, count: s.count + 1)
        return numDecodings(s, 0, &memo)
    }

    private func numDecodings(_ s: String, _ index: Int, _ memo: inout [Int?]) -> Int {
        if index == s.count {
            return 1
        }
        let chars = Array(s)
        if chars[index] == "0" {
            return 0
        }
        if let cached = memo[index] {
            return cached
        }
        let way1 = numDecodings(s, index + 1, &memo)
        var way2 = 0
        if index < s.count - 1, let twoDigit = Int(String(chars[index...index+1])), twoDigit <= 26 {
            way2 = numDecodings(s, index + 2, &memo)
        }
        memo[index] = way1 + way2
        return memo[index]!
    }
}

let solution = Solution()
print(solution.numDecodings("226")) // Output: 3
```

### The End

