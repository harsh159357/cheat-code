# To Lower Case

## Problem Statement

Given a string `s`, return the string in lowercase.

---

## Input

```text
s = "Hello"
```

## Output

```text
"hello"
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun toLowerCase(s: String): String {
        return s.lowercase()
    }
}
```


### Dart

```dart
String toLowerCase(String s) {
  return s.toLowerCase();
}

void main() {
  print(toLowerCase("Hello")); // Output: "hello"
}
```


### C#

```csharp
public class Solution {
    public string ToLowerCase(string s) {
        return s.ToLower();
    }
}
```

### Java

```java
class Solution {
    public String toLowerCase(String s) {
        return s.toLowerCase();
    }
}
```


### Swift

```swift
class Solution {
    func toLowerCase(_ s: String) -> String {
        return s.lowercased()
    }
}
```


### The End