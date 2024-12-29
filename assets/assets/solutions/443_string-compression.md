# String Compression

## Problem Statement

Given an array of characters `chars`, compress it in place. The compressed string should replace the characters in the original array.

The compression uses the following algorithm:

- For a group of consecutive repeating characters in `chars`, replace the group with the character followed by the group's length. If the length of the group is `1`, do not append the length.
- The final result should be placed within the first `writeIndex` characters of `chars`.
- Return `writeIndex`, the new length of the array after compression.

## Input

```text
chars = ['a', 'a', 'b', 'b', 'c', 'c', 'c']
```

## Output

```text
6
```


## Solutions

### Dart

```dart
int compress(List<String> chars) {
  int writeIndex = 0;
  int left = 0;

  for (int right = 0; right < chars.length; right++) {
    if (right == chars.length - 1 || chars[right] != chars[right + 1]) {
      chars[writeIndex++] = chars[left];
      if (right > left) {
        String count = (right - left + 1).toString();
        for (int i = 0; i < count.length; i++) {
          chars[writeIndex++] = count[i];
        }
      }
      left = right + 1;
    }
  }

  return writeIndex;
}
```

### C#

```csharp
public class Solution {
    public int Compress(char[] chars) {
        int writeIndex = 0;
        int left = 0;

        for (int right = 0; right < chars.Length; right++) {
            if (right == chars.Length - 1 || chars[right] != chars[right + 1]) {
                chars[writeIndex++] = chars[left];
                if (right > left) {
                    string count = (right - left + 1).ToString();
                    foreach (char c in count) {
                        chars[writeIndex++] = c;
                    }
                }
                left = right + 1;
            }
        }

        return writeIndex;
    }
}
```

### Java

```java
class Solution {
    public int compress(char[] chars) {
        int writeIndex = 0;
        int left = 0;

        for (int right = 0; right < chars.length; right++) {
            if (right == chars.length - 1 || chars[right] != chars[right + 1]) {
                chars[writeIndex++] = chars[left];
                if (right > left) {
                    String count = String.valueOf(right - left + 1);
                    for (char c : count.toCharArray()) {
                        chars[writeIndex++] = c;
                    }
                }
                left = right + 1;
            }
        }

        return writeIndex;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun compress(chars: CharArray): Int {
        var writeIndex = 0
        var left = 0

        for (right in chars.indices) {
            if (right == chars.size - 1 || chars[right] != chars[right + 1]) {
                chars[writeIndex++] = chars[left]
                if (right > left) {
                    val count = right - left + 1
                    for (ch in count.toString()) {
                        chars[writeIndex++] = ch
                    }
                }
                left = right + 1
            }
        }

        return writeIndex
    }
}
```

### Swift

```swift
class Solution {
    func compress(_ chars: inout [Character]) -> Int {
        var writeIndex = 0
        var left = 0

        for right in 0..<chars.count {
            if right == chars.count - 1 || chars[right] != chars[right + 1] {
                chars[writeIndex] = chars[left]
                writeIndex += 1
                if right > left {
                    let count = String(right - left + 1)
                    for ch in count {
                        chars[writeIndex] = ch
                        writeIndex += 1
                    }
                }
                left = right + 1
            }
        }

        return writeIndex
    }
}
```

### The End