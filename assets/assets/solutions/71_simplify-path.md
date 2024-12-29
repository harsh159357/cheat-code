# Simplify Path

## Problem Statement

Given a string `path`, which is an absolute path (starting with a slash '/') to a file or directory in a Unix-style file system, convert it to the simplified canonical path.

In a Unix-style file system, a period '.' refers to the current directory, a double period '..' moves the directory up a level, and any multiple consecutive slashes (e.g. '//') are treated as a single slash '/'.

The canonical path should have the following format:
- The path starts with a single slash '/'.
- Any two directories are separated by a single slash '/'.
- The path does not end with a trailing '/'.
- The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period '.' or double period '..').

## Input

```text
path = "/home/../usr//bin/"
```

## Output

```text
"/usr/bin"  
(Explanation: The canonical path is "/usr/bin" after simplifying "home", "..", and "//".)
```

## Solutions

### Dart

```dart
String simplifyPath(String path) {
  List<String> stack = [];
  for (String part in path.split('/')) {
    if (part == "" || part == ".") {
      continue;
    } else if (part == "..") {
      if (stack.isNotEmpty) {
        stack.removeLast();
      }
    } else {
      stack.add(part);
    }
  }
  return "/" + stack.join("/");
}

void main() {
  print(simplifyPath("/home/../usr//bin/")); // Output: "/usr/bin"
  print(simplifyPath("/../")); // Output: "/"
  print(simplifyPath("/home//foo/")); // Output: "/home/foo"
}
```

### C#

```csharp
public class Solution {
    public string SimplifyPath(string path) {
        var stack = new Stack<string>();
        foreach (var part in path.Split('/')) {
            if (part == "" || part == ".") {
                continue;
            } else if (part == "..") {
                if (stack.Count > 0) {
                    stack.Pop();
                }
            } else {
                stack.Push(part);
            }
        }
        return "/" + string.Join("/", stack.Reverse());
    }
}
```

### Java

```java
class Solution {
    public String simplifyPath(String path) {
        Stack<String> stack = new Stack<>();
        for (String part : path.split("/")) {
            if (part.isEmpty() || part.equals(".")) {
                continue;
            } else if (part.equals("..")) {
                if (!stack.isEmpty()) {
                    stack.pop();
                }
            } else {
                stack.push(part);
            }
        }
        return "/" + String.join("/", stack);
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun simplifyPath(path: String): String {
        val stack = Stack<String>()
        for (part in path.split('/')) {
            when (part) {
                "", "." -> { /* Do nothing for empty or current directory */ }
                ".." -> stack.takeIf { it.isNotEmpty() }?.pop()
                else -> stack.push(part)
            }
        }
        return "/" + stack.joinToString("/")
    }
}
```

### Swift

```swift
class Solution {
    func simplifyPath(_ path: String) -> String {
        var stack = [String]()
        for part in path.split(separator: "/") {
            if part == "" || part == "." {
                continue
            } else if part == ".." {
                if !stack.isEmpty {
                    stack.removeLast()
                }
            } else {
                stack.append(String(part))
            }
        }
        return "/" + stack.joined(separator: "/")
    }
}

let solution = Solution()
print(solution.simplifyPath("/home/../usr//bin/")) // Output: "/usr/bin"
print(solution.simplifyPath("/../")) // Output: "/"
print(solution.simplifyPath("/home//foo/")) // Output: "/home/foo"
```

### The End

