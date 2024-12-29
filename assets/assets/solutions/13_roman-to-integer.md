# Roman to Integer

## Problem Statement

Given a Roman numeral, convert it to an integer.

## Input

```text
s = "MCMXCIV"
```

## Output

```text
1994  
(Explanation: M = 1000, CM = 900, XC = 90, IV = 4.)
```

## Solutions

### Dart

```dart
int romanToInt(String s) {
  Map<String, int> romanToIntMap = {
    'I': 1,
    'V': 5,
    'X': 10,
    'L': 50,
    'C': 100,
    'D': 500,
    'M': 1000
  };

  int result = 0;
  int prevValue = 0;

  for (int i = s.length - 1; i >= 0; i--) {
    int value = romanToIntMap[s[i]]!;
    if (value < prevValue) {
      result -= value;
    } else {
      result += value;
    }
    prevValue = value;
  }

  return result;
}

void main() {
  print(romanToInt("III"));    // Output: 3
  print(romanToInt("LVIII")); // Output: 58
  print(romanToInt("MCMXCIV")); // Output: 1994
}
```

### C#

```csharp
public class Solution {
    public int RomanToInt(string s) {
        var romanToIntMap = new Dictionary<char, int> {
            {'I', 1}, {'V', 5}, {'X', 10}, {'L', 50}, {'C', 100}, {'D', 500}, {'M', 1000}
        };

        int result = 0;
        int prevValue = 0;

        for (int i = s.Length - 1; i >= 0; i--) {
            int value = romanToIntMap[s[i]];
            if (value < prevValue) {
                result -= value;
            } else {
                result += value;
            }
            prevValue = value;
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> romanToIntMap = Map.of(
            'I', 1, 'V', 5, 'X', 10, 'L', 50, 'C', 100, 'D', 500, 'M', 1000
        );

        int result = 0;
        int prevValue = 0;

        for (int i = s.length() - 1; i >= 0; i--) {
            int value = romanToIntMap.get(s.charAt(i));
            if (value < prevValue) {
                result -= value;
            } else {
                result += value;
            }
            prevValue = value;
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun romanToInt(s: String): Int {
        val romanToIntMap = mapOf(
            'I' to 1, 'V' to 5, 'X' to 10, 'L' to 50, 'C' to 100, 'D' to 500, 'M' to 1000
        )

        var result = 0
        var prevValue = 0

        for (i in s.length - 1 downTo 0) {
            val value = romanToIntMap[s[i]]!!
            if (value < prevValue) {
                result -= value
            } else {
                result += value
            }
            prevValue = value
        }

        return result
    }
}

fun main() {
    println(Solution().romanToInt("III"))    // Output: 3
    println(Solution().romanToInt("LVIII")) // Output: 58
    println(Solution().romanToInt("MCMXCIV")) // Output: 1994
}
```

### Swift

```swift
class Solution {
    func romanToInt(_ s: String) -> Int {
        let romanToIntMap: [Character: Int] = [
            'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000
        ]

        var result = 0
        var prevValue = 0

        for char in s.reversed() {
            let value = romanToIntMap[char]!
            if value < prevValue {
                result -= value
            } else {
                result += value
            }
            prevValue = value
        }

        return result
    }
}

let solution = Solution()
print(solution.romanToInt("III"))    // Output: 3
print(solution.romanToInt("LVIII")) // Output: 58
print(solution.romanToInt("MCMXCIV")) // Output: 1994
```


### The End

