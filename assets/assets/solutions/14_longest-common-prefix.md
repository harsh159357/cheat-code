# Longest Common Prefix

## Problem Statement

Write a function to find the longest common prefix string amongst an array of strings. If there is no common prefix, return an empty string `""`.

## Input

```text
strs = ["flower", "flow", "flight"]
```

## Output

```text
"fl"  
(Explanation: The longest common prefix is "fl".)
```

## Solutions

### Dart

```dart
String longestCommonPrefix(List<String> strs) {
  if (strs.isEmpty) return "";

  String prefix = strs[0];

  for (int i = 1; i < strs.length; i++) {
    while (!strs[i].startsWith(prefix)) {
      prefix = prefix.substring(0, prefix.length - 1);
      if (prefix.isEmpty) return "";
    }
  }

  return prefix;
}

void main() {
  print(longestCommonPrefix(["flower", "flow", "flight"])); // Output: "fl"
  print(longestCommonPrefix(["dog", "racecar", "car"]));    // Output: ""
}
```

### C#

```csharp
public class Solution {
    public string LongestCommonPrefix(string[] strs) {
        if (strs.Length == 0) return "";

        string prefix = strs[0];

        for (int i = 1; i < strs.Length; i++) {
            while (!strs[i].StartsWith(prefix)) {
                prefix = prefix.Substring(0, prefix.Length - 1);
                if (prefix == "") return "";
            }
        }

        return prefix;
    }
}
```

### Java

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) return "";

        String prefix = strs[0];

        for (int i = 1; i < strs.length; i++) {
            while (!strs[i].startsWith(prefix)) {
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix.isEmpty()) return "";
            }
        }

        return prefix;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun longestCommonPrefix(strs: Array<String>): String {
        if (strs.isEmpty()) return ""

        var prefix = strs[0]

        for (i in 1 until strs.size) {
            while (!strs[i].startsWith(prefix)) {
                prefix = prefix.substring(0, prefix.length - 1)
                if (prefix.isEmpty()) return ""
            }
        }

        return prefix
    }
}

fun main() {
    val strs1 = arrayOf("flower", "flow", "flight")
    println(Solution().longestCommonPrefix(strs1)) // Output: "fl"

    val strs2 = arrayOf("dog", "racecar", "car")
    println(Solution().longestCommonPrefix(strs2)) // Output: ""
}
```

### Swift

```swift
class Solution {
    func longestCommonPrefix(_ strs: [String]) -> String {
        if strs.isEmpty { return "" }

        var prefix = strs[0]

        for i in 1..<strs.count {
            while !strs[i].hasPrefix(prefix) {
                prefix.removeLast()
                if prefix.isEmpty { return "" }
            }
        }

        return prefix
    }
}

let solution = Solution()
print(solution.longestCommonPrefix(["flower", "flow", "flight"])) // Output: "fl"
print(solution.longestCommonPrefix(["dog", "racecar", "car"]))    // Output: ""
```


### The End

