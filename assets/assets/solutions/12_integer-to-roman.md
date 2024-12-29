# Integer to Roman

## Problem Statement

Given an integer, convert it to a Roman numeral.

## Input

```text
num = 1994
```

## Output

```text
"MCMXCIV"  
(Explanation: 1000 = M, 900 = CM, 90 = XC, 4 = IV.)
```

## Solutions

### Dart

```dart
String intToRoman(int num) {
  List<String> romanSymbols = [
    "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"
  ];
  List<int> values = [
    1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1
  ];

  String result = "";
  for (int i = 0; i < values.length; i++) {
    while (num >= values[i]) {
      result += romanSymbols[i];
      num -= values[i];
    }
  }

  return result;
}

void main() {
  print(intToRoman(3));    // Output: "III"
  print(intToRoman(58));   // Output: "LVIII"
  print(intToRoman(1994)); // Output: "MCMXCIV"
}
```

### C#

```csharp
public class Solution {
    public string IntToRoman(int num) {
        string[] romanSymbols = { "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I" };
        int[] values = { 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 };

        string result = "";
        for (int i = 0; i < values.Length; i++) {
            while (num >= values[i]) {
                result += romanSymbols[i];
                num -= values[i];
            }
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public String intToRoman(int num) {
        String[] romanSymbols = { "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I" };
        int[] values = { 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 };

        StringBuilder result = new StringBuilder();
        for (int i = 0; i < values.length; i++) {
            while (num >= values[i]) {
                result.append(romanSymbols[i]);
                num -= values[i];
            }
        }

        return result.toString();
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun intToRoman(num: Int): String {
        val romanSymbols = arrayOf("M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I")
        val values = arrayOf(1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1)

        var result = ""
        var remainingNum = num
        for (i in values.indices) {
            while (remainingNum >= values[i]) {
                result += romanSymbols[i]
                remainingNum -= values[i]
            }
        }
        return result
    }
}

fun main() {
    println(Solution().intToRoman(3))    // Output: "III"
    println(Solution().intToRoman(58))   // Output: "LVIII"
    println(Solution().intToRoman(1994)) // Output: "MCMXCIV"
}
```

### Swift

```swift
class Solution {
    func intToRoman(_ num: Int) -> String {
        let romanSymbols = ["M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"]
        let values = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]

        var result = ""
        var remainingNum = num
        for i in 0..<values.count {
            while remainingNum >= values[i] {
                result += romanSymbols[i]
                remainingNum -= values[i]
            }
        }
        return result
    }
}

let solution = Solution()
print(solution.intToRoman(3))    // Output: "III"
print(solution.intToRoman(58))   // Output: "LVIII"
print(solution.intToRoman(1994)) // Output: "MCMXCIV"
```


### The End

