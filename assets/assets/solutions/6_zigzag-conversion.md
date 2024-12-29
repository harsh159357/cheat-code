# Zigzag Conversion

## Problem Statement

The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this:

```text
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`.

Write the code that will take a string and make this conversion given a number of rows:

`string convert(string s, int numRows);`

## Input

```text
s = "PAYPALISHIRING"  
numRows = 3
```

## Output

```text
"PAHNAPLSIIGYIR"
```

## Solutions

### Dart

```dart
String convert(String s, int numRows) {
  if (numRows == 1 || numRows >= s.length) return s;

  List<StringBuffer> rows = List.generate(numRows, (_) => StringBuffer());
  int currentRow = 0;
  bool goingDown = false;

  for (int i = 0; i < s.length; i++) {
    rows[currentRow].write(s[i]);
    if (currentRow == 0 || currentRow == numRows - 1) goingDown = !goingDown;
    currentRow += goingDown ? 1 : -1;
  }

  return rows.map((e) => e.toString()).join();
}

void main() {
  print(convert("PAYPALISHIRING", 3)); // Output: "PAHNAPLSIIGYIR"
  print(convert("PAYPALISHIRING", 4)); // Output: "PINALSIGYAHRPI"
  print(convert("A", 1)); // Output: "A"
}
```

### C#

```csharp
public class Solution {
    public string Convert(string s, int numRows) {
        if (numRows == 1 || numRows >= s.Length) return s;

        var rows = new List<StringBuilder>(new StringBuilder[numRows].Select(_ => new StringBuilder()));
        int currentRow = 0;
        bool goingDown = false;

        foreach (char c in s) {
            rows[currentRow].Append(c);
            if (currentRow == 0 || currentRow == numRows - 1) goingDown = !goingDown;
            currentRow += goingDown ? 1 : -1;
        }

        return string.Concat(rows);
    }
}
```

### Java

```java
class Solution {
    public String convert(String s, int numRows) {
        if (numRows == 1 || numRows >= s.length()) return s;

        List<StringBuilder> rows = new ArrayList<>();
        for (int i = 0; i < Math.min(numRows, s.length()); i++) {
            rows.add(new StringBuilder());
        }

        int currentRow = 0;
        boolean goingDown = false;

        for (char c : s.toCharArray()) {
            rows.get(currentRow).append(c);
            if (currentRow == 0 || currentRow == numRows - 1) goingDown = !goingDown;
            currentRow += goingDown ? 1 : -1;
        }

        StringBuilder result = new StringBuilder();
        for (StringBuilder row : rows) {
            result.append(row);
        }
        return result.toString();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun convert(s: String, numRows: Int): String {
        if (numRows == 1 || numRows >= s.length) return s

        val rows = Array(numRows) { StringBuilder() }
        var currentRow = 0
        var goingDown = false

        for (char in s) {
            rows[currentRow].append(char)
            if (currentRow == 0 || currentRow == numRows - 1) goingDown = !goingDown
            currentRow += if (goingDown) 1 else -1
        }

        return rows.joinToString(separator = "") { it.toString() }
    }
}

fun main() {
    println(Solution().convert("PAYPALISHIRING", 3)) // Output: "PAHNAPLSIIGYIR"
    println(Solution().convert("PAYPALISHIRING", 4)) // Output: "PINALSIGYAHRPI"
    println(Solution().convert("A", 1)) // Output: "A"
}
```

### Swift

```swift
class Solution {
    func convert(_ s: String, _ numRows: Int) -> String {
        if numRows == 1 || numRows >= s.count { return s }

        var rows = [String](repeating: "", count: min(numRows, s.count))
        var currentRow = 0
        var goingDown = false

        for char in s {
            rows[currentRow] += String(char)
            if currentRow == 0 || currentRow == numRows - 1 {
                goingDown.toggle()
            }
            currentRow += goingDown ? 1 : -1
        }

        return rows.joined()
    }
}

let solution = Solution()
print(solution.convert("PAYPALISHIRING", 3)) // Output: "PAHNAPLSIIGYIR"
print(solution.convert("PAYPALISHIRING", 4)) // Output: "PINALSIGYAHRPI"
print(solution.convert("A", 1)) // Output: "A"
```

### The End

