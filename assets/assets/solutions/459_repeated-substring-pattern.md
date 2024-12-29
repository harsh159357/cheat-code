# Repeated Substring Pattern

## Problem Statement

Given a string `s`, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.

Return `true` if the string can be constructed using this way, otherwise return `false`.

## Input

```text
s = "abab"
```

## Output

```text
true
```


## Solutions

### Dart

```dart
bool repeatedSubstringPattern(String s) {
  int n = s.length;
  for (int i = 1; i <= n ~/ 2; i++) {
    if (n % i == 0) {
      String substring = s.substring(0, i);
      String repeated = substring * (n ~/ i);
      if (repeated == s) {
        return true;
      }
    }
  }
  return false;
}

void main() {
  print(repeatedSubstringPattern("abab")); // Output: true
  print(repeatedSubstringPattern("aba"));  // Output: false
}
```

### C#

```csharp
public class Solution {
    public bool RepeatedSubstringPattern(string s) {
        int n = s.Length;
        for (int i = 1; i <= n / 2; i++) {
            if (n % i == 0) {
                string substring = s.Substring(0, i);
                string repeated = string.Concat(Enumerable.Repeat(substring, n / i));
                if (repeated == s) {
                    return true;
                }
            }
        }
        return false;
    }
}
```

### Java

```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        int n = s.length();
        for (int i = 1; i <= n / 2; i++) {
            if (n % i == 0) {
                String substring = s.substring(0, i);
                StringBuilder sb = new StringBuilder();
                for (int j = 0; j < n / i; j++) {
                    sb.append(substring);
                }
                if (sb.toString().equals(s)) {
                    return true;
                }
            }
        }
        return false;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun repeatedSubstringPattern(s: String): Boolean {
        val n = s.length
        for (i in 1..n / 2) {
            if (n % i == 0) {
                val substring = s.substring(0, i)
                val sb = StringBuilder()
                repeat(n / i) {
                    sb.append(substring)
                }
                if (sb.toString() == s) {
                    return true
                }
            }
        }
        return false
    }
}

fun main() {
    val solution = Solution()
    println(solution.repeatedSubstringPattern("abab")) // Output: true
    println(solution.repeatedSubstringPattern("aba"))  // Output: false
}
```

### Swift

```swift
class Solution {
    func repeatedSubstringPattern(_ s: String) -> Bool {
        let n = s.count
        for i in 1...n / 2 {
            if n % i == 0 {
                let substring = String(s.prefix(i))
                let repeated = String(repeating: substring, count: n / i)
                if repeated == s {
                    return true
                }
            }
        }
        return false
    }
}

// Example usage
let solution = Solution()
print(solution.repeatedSubstringPattern("abab")) // Output: true
print(solution.repeatedSubstringPattern("aba"))  // Output: false
```

### The End