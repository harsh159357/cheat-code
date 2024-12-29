# Add Binary

## Problem Statement

Given two binary strings `a` and `b`, return their sum as a binary string.

## Input

```text
a = "11", b = "1"
```

## Output

```text
"100"  
(Explanation: Adding binary 11 and 1 gives binary 100.)
```

## Solutions

### Dart

```dart
String addBinary(String a, String b) {
  StringBuffer sb = StringBuffer();
  int i = a.length - 1, j = b.length - 1, carry = 0;

  while (i >= 0 || j >= 0 || carry > 0) {
    int sum = (i >= 0 ? a.codeUnitAt(i--) - '0'.codeUnitAt(0) : 0) +
              (j >= 0 ? b.codeUnitAt(j--) - '0'.codeUnitAt(0) : 0) + carry;
    sb.write(sum % 2);
    carry = sum ~/ 2;
  }

  return sb.toString().split('').reversed.join();
}

void main() {
  print(addBinary("11", "1")); // Output: "100"
  print(addBinary("1010", "1011")); // Output: "10101"
}
```

### C#

```csharp
public class Solution {
    public string AddBinary(string a, string b) {
        StringBuilder sb = new StringBuilder();
        int i = a.Length - 1, j = b.Length - 1, carry = 0;

        while (i >= 0 || j >= 0 || carry > 0) {
            int sum = (i >= 0 ? a[i--] - '0' : 0) +
                      (j >= 0 ? b[j--] - '0' : 0) + carry;
            sb.Append(sum % 2);
            carry = sum / 2;
        }

        char[] result = sb.ToString().ToCharArray();
        Array.Reverse(result);
        return new string(result);
    }
}
```

### Java

```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int i = a.length() - 1, j = b.length() - 1, carry = 0;

        while (i >= 0 || j >= 0 || carry > 0) {
            int sum = (i >= 0 ? a.charAt(i--) - '0' : 0) +
                      (j >= 0 ? b.charAt(j--) - '0' : 0) + carry;
            sb.append(sum % 2);
            carry = sum / 2;
        }

        return sb.reverse().toString();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun addBinary(a: String, b: String): String {
        val sb = StringBuilder()
        var i = a.length - 1
        var j = b.length - 1
        var carry = 0
        
        while (i >= 0 || j >= 0 || carry > 0) {
            val sum = (if (i >= 0) a[i--] - '0' else 0) +
                      (if (j >= 0) b[j--] - '0' else 0) + carry
            sb.append(sum % 2)
            carry = sum / 2
        }

        return sb.reverse().toString()
    }
}
```

### Swift

```swift
class Solution {
    func addBinary(_ a: String, _ b: String) -> String {
        var result = ""
        var i = a.count - 1
        var j = b.count - 1
        var carry = 0

        let aChars = Array(a)
        let bChars = Array(b)

        while i >= 0 || j >= 0 || carry > 0 {
            let sum = (i >= 0 ? Int(String(aChars[i--]))! : 0) +
                      (j >= 0 ? Int(String(bChars[j--]))! : 0) + carry
            result = "\(sum % 2)" + result
            carry = sum / 2
        }

        return result
    }
}

let solution = Solution()
print(solution.addBinary("11", "1")) // Output: "100"
print(solution.addBinary("1010", "1011")) // Output: "10101"
```

### The End

