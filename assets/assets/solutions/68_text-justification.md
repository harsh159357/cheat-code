# Text Justification

## Problem Statement

Given an array of words and a width `maxWidth`, format the text such that each line has exactly `maxWidth` characters and is fully (left and right) justified.

## Input

```text
words = ["This", "is", "an", "example", "of", "text", "justification."], maxWidth = 16
```

## Output

```text
[
"This    is    an",
"example  of text",
"justification.  "
]
```

## Solutions

### Dart

```dart
List<String> fullJustify(List<String> words, int maxWidth) {
  List<String> result = [];
  int index = 0;

  while (index < words.length) {
    int lineStart = index;
    int lineEnd = lineStart;
    int lineLength = words[lineStart].length;

    while (lineEnd + 1 < words.length &&
           lineLength + words[lineEnd + 1].length + (lineEnd + 1 - lineStart) <= maxWidth) {
      lineEnd++;
      lineLength += words[lineEnd].length;
    }

    int spaces = maxWidth - lineLength;
    int numGaps = lineEnd - lineStart;
    StringBuffer lineBuffer = StringBuffer();

    if (lineEnd == words.length - 1 || numGaps == 0) {
      for (int i = lineStart; i <= lineEnd; i++) {
        lineBuffer.write(words[i]);
        if (i < lineEnd) lineBuffer.write(' ');
      }
      lineBuffer.write(' ' * (spaces - numGaps));
    } else {
      int spacesPerGap = spaces ~/ numGaps;
      int extraSpaces = spaces % numGaps;

      for (int i = lineStart; i <= lineEnd; i++) {
        lineBuffer.write(words[i]);
        if (i < lineEnd) {
          lineBuffer.write(' ' * spacesPerGap);
          if (i - lineStart < extraSpaces) {
            lineBuffer.write(' ');
          }
        }
      }
    }

    result.add(lineBuffer.toString());
    index = lineEnd + 1;
  }

  return result;
}

void main() {
  print(fullJustify(["This", "is", "an", "example", "of", "text", "justification."], 16));
  print(fullJustify(["What", "must", "be", "acknowledgment", "shall", "be"], 16));
  print(fullJustify(["Science", "is", "what", "we", "understand", "well", "enough", "to", "explain", "to", "a", "computer.", "Art", "is", "everything", "else", "we", "do"], 20));
}
```

### C#

```csharp
public class Solution {
    public IList<string> FullJustify(string[] words, int maxWidth) {
        var result = new List<string>();
        int index = 0;

        while (index < words.Length) {
            int lineStart = index;
            int lineEnd = lineStart;
            int lineLength = words[lineStart].Length;

            while (lineEnd + 1 < words.Length &&
                   lineLength + words[lineEnd + 1].Length + (lineEnd + 1 - lineStart) <= maxWidth) {
                lineEnd++;
                lineLength += words[lineEnd].Length;
            }

            int spaces = maxWidth - lineLength;
            int numGaps = lineEnd - lineStart;
            var lineBuffer = new StringBuilder();

            if (lineEnd == words.Length - 1 || numGaps == 0) {
                for (int i = lineStart; i <= lineEnd; i++) {
                    lineBuffer.Append(words[i]);
                    if (i < lineEnd) lineBuffer.Append(" ");
                }
                lineBuffer.Append(new string(' ', spaces - numGaps));
            } else {
                int spacesPerGap = spaces / numGaps;
                int extraSpaces = spaces % numGaps;

                for (int i = lineStart; i <= lineEnd; i++) {
                    lineBuffer.Append(words[i]);
                    if (i < lineEnd) {
                        lineBuffer.Append(new string(' ', spacesPerGap));
                        if (i - lineStart < extraSpaces) {
                            lineBuffer.Append(' ');
                        }
                    }
                }
            }

            result.Add(lineBuffer.ToString());
            index = lineEnd + 1;
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public List<String> fullJustify(String[] words, int maxWidth) {
        List<String> result = new ArrayList<>();
        int index = 0;

        while (index < words.length) {
            int lineStart = index;
            int lineEnd = lineStart;
            int lineLength = words[lineStart].length();

            while (lineEnd + 1 < words.length &&
                   lineLength + words[lineEnd + 1].length() + (lineEnd + 1 - lineStart) <= maxWidth) {
                lineEnd++;
                lineLength += words[lineEnd].length();
            }

            int spaces = maxWidth - lineLength;
            int numGaps = lineEnd - lineStart;
            StringBuilder lineBuilder = new StringBuilder();

            if (lineEnd == words.length - 1 || numGaps == 0) {
                for (int i = lineStart; i <= lineEnd; i++) {
                    lineBuilder.append(words[i]);
                    if (i < lineEnd) lineBuilder.append(" ");
                }
                lineBuilder.append(" ".repeat(spaces - numGaps));
            } else {
                int spacesPerGap = spaces / numGaps;
                int extraSpaces = spaces % numGaps;

                for (int i = lineStart; i <= lineEnd; i++) {
                    lineBuilder.append(words[i]);
                    if (i < lineEnd) {
                        lineBuilder.append(" ".repeat(spacesPerGap));
                        if (i - lineStart < extraSpaces) {
                            lineBuilder.append(" ");
                        }
                    }
                }
            }

            result.add(lineBuilder.toString());
            index = lineEnd + 1;
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun fullJustify(words: Array<String>, maxWidth: Int): List<String> {
        val result = mutableListOf<String>()
        var index = 0

        while (index < words.size) {
            val lineStart = index
            var lineEnd = lineStart
            var lineLength = words[lineStart].length

            while (lineEnd + 1 < words.size &&
                   lineLength + words[lineEnd + 1].length + (lineEnd + 1 - lineStart) <= maxWidth) {
                lineEnd++
                lineLength += words[lineEnd].length
            }

            val spaces = maxWidth - lineLength
            val numGaps = lineEnd - lineStart
            val lineBuilder = StringBuilder()

            if (lineEnd == words.size - 1 || numGaps == 0) {
                for (i in lineStart..lineEnd) {
                    lineBuilder.append(words[i])
                    if (i < lineEnd) lineBuilder.append(" ")
                }
                repeat(spaces - numGaps) {
                    lineBuilder.append(" ")
                }
            } else {
                val spacesPerGap = spaces / numGaps
                val extraSpaces = spaces % numGaps

                for (i in lineStart..lineEnd) {
                    lineBuilder.append(words[i])
                    if (i < lineEnd) {
                        repeat(spacesPerGap) {
                            lineBuilder.append(" ")
                        }
                        if (i - lineStart < extraSpaces) {
                            lineBuilder.append(" ")
                        }
                    }
                }
            }

            result.add(lineBuilder.toString())
            index = lineEnd + 1
        }

        return result
    }
}
```

### Swift

```swift
class Solution {
    func fullJustify(_ words: [String], _ maxWidth: Int) -> [String] {
        var result = [String]()
        var index = 0

        while index < words.count {
            let lineStart = index
            var lineEnd = lineStart
            var lineLength = words[lineStart].count

            while lineEnd + 1 < words.count &&
                  lineLength + words[lineEnd + 1].count + (lineEnd + 1 - lineStart) <= maxWidth {
                lineEnd += 1
                lineLength += words[lineEnd].count
            }

            let spaces = maxWidth - lineLength
            let numGaps = lineEnd - lineStart
            var line = ""

            if lineEnd == words.count - 1 || numGaps == 0 {
                for i in lineStart...lineEnd {
                    line += words[i]
                    if i < lineEnd { line += " " }
                }
                line += String(repeating: " ", spaces - numGaps)
            } else {
                let spacesPerGap = spaces / numGaps
                let extraSpaces = spaces % numGaps

                for i in lineStart...lineEnd {
                    line += words[i]
                    if i < lineEnd {
                        line += String(repeating: " ", spacesPerGap)
                        if i - lineStart < extraSpaces {
                            line += " "
                        }
                    }
                }
            }

            result.append(line)
            index = lineEnd + 1
        }

        return result
    }
}

let solution = Solution()
print(solution.fullJustify(["This", "is", "an", "example", "of", "text", "justification."], 16))
print(solution.fullJustify(["What", "must", "be", "acknowledgment", "shall", "be"], 16))
print(solution.fullJustify(["Science", "is", "what", "we", "understand", "well", "enough", "to", "explain", "to", "a", "computer.", "Art", "is", "everything", "else", "we", "do"], 20))
```
### The End

