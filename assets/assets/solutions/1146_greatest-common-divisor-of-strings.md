# Greatest Common Divisor of Strings

## Problem Statement

Given two strings `str1` and `str2`, return the greatest common divisor (GCD) of the two strings. The GCD of two strings is the largest string `x` such that `x` divides both `str1` and `str2`.

## Input

```text
str1 = "ABCABC"
str2 = "ABC"
```

## Output

```text
"ABC"
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun gcdOfStrings(str1: String, str2: String): String {
        if (str1 + str2 != str2 + str1) return ""
        fun gcd(a: Int, b: Int): Int = if (b == 0) a else gcd(b, a % b)
        return str1.substring(0, gcd(str1.length, str2.length))
    }
}
```

### Dart

```dart
String gcdOfStrings(String str1, String str2) {
  if (str1 + str2 != str2 + str1) return "";
  int gcd(int a, int b) => b == 0 ? a : gcd(b, a % b);
  return str1.substring(0, gcd(str1.length, str2.length));
}
```

### C#

```csharp
public class Solution {
    public string GcdOfStrings(string str1, string str2) {
        if (str1 + str2 != str2 + str1) return "";
        int Gcd(int a, int b) => b == 0 ? a : Gcd(b, a % b);
        return str1.Substring(0, Gcd(str1.Length, str2.Length));
    }
}
```

### Java

```java
class Solution {
    public String gcdOfStrings(String str1, String str2) {
        if (!(str1 + str2).equals(str2 + str1)) return "";
        int gcd(int a, int b) {
            return b == 0 ? a : gcd(b, a % b);
        }
        return str1.substring(0, gcd(str1.length(), str2.length()));
    }
}
```

### Swift

```swift
class Solution {
    func gcdOfStrings(_ str1: String, _ str2: String) -> String {
        if str1 + str2 != str2 + str1 { return "" }
        func gcd(_ a: Int, _ b: Int) -> Int {
            return b == 0 ? a : gcd(b, a % b)
        }
        let length = gcd(str1.count, str2.count)
        return String(str1.prefix(length))
    }
}
```

### The End