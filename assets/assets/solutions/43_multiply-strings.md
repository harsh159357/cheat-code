# Multiply Strings

## Problem Statement

Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.

You must not use any built-in BigInteger library or convert the inputs to integer directly.

## Input

```text
num1 = "123", num2 = "456"
```

## Output

```text
"56088"  
(Explanation: The product of 123 and 456 is 56088.)
```

## Solutions

### Dart

```dart
String multiply(String num1, String num2) {
  if (num1 == "0" || num2 == "0") return "0";

  List<int> result = List.filled(num1.length + num2.length, 0);

  for (int i = num1.length - 1; i >= 0; i--) {
    for (int j = num2.length - 1; j >= 0; j--) {
      int product = (num1[i].codeUnitAt(0) - '0'.codeUnitAt(0)) *
          (num2[j].codeUnitAt(0) - '0'.codeUnitAt(0));
      int sum = product + result[i + j + 1];

      result[i + j] += sum ~/ 10;
      result[i + j + 1] = sum % 10;
    }
  }

  StringBuffer sb = StringBuffer();
  for (int digit in result) {
    if (!(sb.isEmpty && digit == 0)) sb.write(digit);
  }

  return sb.toString();
}

void main() {
  print(multiply("123", "456")); // Output: "56088"
  print(multiply("2", "3")); // Output: "6"
}
```

### C#

```csharp
public class Solution {
    public string Multiply(string num1, string num2) {
        if (num1 == "0" || num2 == "0") return "0";

        int m = num1.Length, n = num2.Length;
        int[] result = new int[m + n];

        for (int i = m - 1; i >= 0; i--) {
            for (int j = n - 1; j >= 0; j--) {
                int product = (num1[i] - '0') * (num2[j] - '0');
                int sum = product + result[i + j + 1];

                result[i + j] += sum / 10;
                result[i + j + 1] = sum % 10;
            }
        }

        StringBuilder sb = new StringBuilder();
        foreach (int digit in result) {
            if (!(sb.Length == 0 && digit == 0)) sb.Append(digit);
        }

        return sb.ToString();
    }
}
```

### Java

```java
class Solution {
    public String multiply(String num1, String num2) {
        if (num1.equals("0") || num2.equals("0")) return "0";

        int m = num1.length(), n = num2.length();
        int[] result = new int[m + n];

        for (int i = m - 1; i >= 0; i--) {
            for (int j = n - 1; j >= 0; j--) {
                int product = (num1.charAt(i) - '0') * (num2.charAt(j) - '0');
                int sum = product + result[i + j + 1];

                result[i + j] += sum / 10;
                result[i + j + 1] = sum % 10;
            }
        }

        StringBuilder sb = new StringBuilder();
        for (int digit : result) {
            if (!(sb.length() == 0 && digit == 0)) sb.append(digit);
        }

        return sb.toString();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun multiply(num1: String, num2: String): String {
        if (num1 == "0" || num2 == "0") return "0"

        val m = num1.length
        val n = num2.length
        val result = IntArray(m + n)

        for (i in m - 1 downTo 0) {
            for (j in n - 1 downTo 0) {
                val product = (num1[i] - '0') * (num2[j] - '0')
                val sum = product + result[i + j + 1]

                result[i + j] += sum / 10
                result[i + j + 1] = sum % 10
            }
        }

        val sb = StringBuilder()
        for (digit in result) {
            if (!(sb.isEmpty() && digit == 0)) {
                sb.append(digit)
            }
        }

        return sb.toString()
    }
}
```

### Swift

```swift
class Solution {
    func multiply(_ num1: String, _ num2: String) -> String {
        if num1 == "0" || num2 == "0" { return "0" }

        let m = num1.count
        let n = num2.count
        var result = [Int](repeating: 0, count: m + n)

        let num1Array = Array(num1)
        let num2Array = Array(num2)

        for i in stride(from: m - 1, through: 0, by: -1) {
            for j in stride(from: n - 1, through: 0, by: -1) {
                let product = Int(String(num1Array[i]))! * Int(String(num2Array[j]))!
                let sum = product + result[i + j + 1]

                result[i + j] += sum / 10
                result[i + j + 1] = sum % 10
            }
        }

        var sb = ""
        for digit in result {
            if !(sb.isEmpty && digit == 0) {
                sb += String(digit)
            }
        }

        return sb
    }
}

let solution = Solution()
print(solution.multiply("123", "456")) // Output: "56088"
print(solution.multiply("2", "3")) // Output: "6"
```


### The End

