# Removing Stars from a String

## Problem Statement

You are given a string `s` containing letters and stars `'*'`.  
In one operation, you can:
- Remove the closest non-star character to the left of a star, and remove the star itself.

Return the string after all stars have been processed.

## Input

```text
s = "leet**cod*e"
```

## Output

```text
"lecoe"
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun removeStars(s: String): String {
        val string = StringBuilder()

        for (c in s) {
            if (c != '*') {
                string.append(c)
            } else {
                string.setLength(string.length - 1)
            }
        }

        return string.toString()
    }
}

fun main() {
    val s = "leet**cod*e"
    println(Solution().removeStars(s)) // Output: "lecoe"
}
```

### Dart

```dart
String removeStars(String s) {
  StringBuffer result = StringBuffer();

  for (int i = 0; i < s.length; i++) {
    if (s[i] != '*') {
      result.write(s[i]);
    } else {
      result.length = result.length - 1;
    }
  }

  return result.toString();
}

void main() {
  String s = "leet**cod*e";
  print(removeStars(s)); // Output: "lecoe"
}
```

### C#

```csharp
public class Solution {
    public string RemoveStars(string s) {
        var result = new StringBuilder();

        foreach (char c in s) {
            if (c != '*') {
                result.Append(c);
            } else {
                result.Length--;
            }
        }

        return result.ToString();
    }
}
```

### Java

```java
class Solution {
    public String removeStars(String s) {
        StringBuilder result = new StringBuilder();

        for (char c : s.toCharArray()) {
            if (c != '*') {
                result.append(c);
            } else {
                result.setLength(result.length() - 1);
            }
        }

        return result.toString();
    }
}
```

### Swift

```swift
class Solution {
    func removeStars(_ s: String) -> String {
        var result = [Character]()

        for char in s {
            if char != "*" {
                result.append(char)
            } else {
                result.removeLast()
            }
        }

        return String(result)
    }
}

let s = "leet**cod*e"
print(Solution().removeStars(s)) // Output: "lecoe"
```

### The End