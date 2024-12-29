# Letter Combinations of a Phone Number

## Problem Statement

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

```text
2 -> "abc"
3 -> "def"
4 -> "ghi"
5 -> "jkl"
6 -> "mno"
7 -> "pqrs"
8 -> "tuv"
9 -> "wxyz"
```

## Input

```text
digits = "23"
```

## Output

```text
["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]
```

## Solutions

### Dart

```dart
List<String> letterCombinations(String digits) {
  if (digits.isEmpty) return [];

  final Map<String, List<String>> phoneMap = {
    "2": ["a", "b", "c"],
    "3": ["d", "e", "f"],
    "4": ["g", "h", "i"],
    "5": ["j", "k", "l"],
    "6": ["m", "n", "o"],
    "7": ["p", "q", "r", "s"],
    "8": ["t", "u", "v"],
    "9": ["w", "x", "y", "z"]
  };

  List<String> result = [];

  void backtrack(String combination, String nextDigits) {
    if (nextDigits.isEmpty) {
      result.add(combination);
    } else {
      String digit = nextDigits[0];
      List<String> letters = phoneMap[digit]!;
      for (String letter in letters) {
        backtrack(combination + letter, nextDigits.substring(1));
      }
    }
  }

  backtrack("", digits);
  return result;
}

void main() {
  print(letterCombinations("23")); // Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]
}
```

### C#

```csharp
public class Solution {
    public IList<string> LetterCombinations(string digits) {
        if (digits.Length == 0) return new List<string>();

        var phoneMap = new Dictionary<char, string> {
            {'2', "abc"}, {'3', "def"}, {'4', "ghi"}, {'5', "jkl"},
            {'6', "mno"}, {'7', "pqrs"}, {'8', "tuv"}, {'9', "wxyz"}
        };

        var result = new List<string>();

        void Backtrack(string combination, string nextDigits) {
            if (nextDigits.Length == 0) {
                result.Add(combination);
            } else {
                char digit = nextDigits[0];
                string letters = phoneMap[digit];
                foreach (var letter in letters) {
                    Backtrack(combination + letter, nextDigits.Substring(1));
                }
            }
        }

        Backtrack("", digits);
        return result;
    }
}
```

### Java

```java
class Solution {
    public List<String> letterCombinations(String digits) {
        if (digits.isEmpty()) return new ArrayList<>();

        Map<Character, String> phoneMap = Map.of(
            '2', "abc", '3', "def", '4', "ghi", '5', "jkl",
            '6', "mno", '7', "pqrs", '8', "tuv", '9', "wxyz"
        );

        List<String> result = new ArrayList<>();

        void backtrack(String combination, String nextDigits) {
            if (nextDigits.isEmpty()) {
                result.add(combination);
            } else {
                char digit = nextDigits.charAt(0);
                String letters = phoneMap.get(digit);
                for (char letter : letters.toCharArray()) {
                    backtrack(combination + letter, nextDigits.substring(1));
                }
            }
        }

        backtrack("", digits);
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun letterCombinations(digits: String): List<String> {
        if (digits.isEmpty()) return emptyList()

        val phoneMap = mapOf(
            '2' to listOf("a", "b", "c"),
            '3' to listOf("d", "e", "f"),
            '4' to listOf("g", "h", "i"),
            '5' to listOf("j", "k", "l"),
            '6' to listOf("m", "n", "o"),
            '7' to listOf("p", "q", "r", "s"),
            '8' to listOf("t", "u", "v"),
            '9' to listOf("w", "x", "y", "z")
        )

        val result = mutableListOf<String>()
        backtrack("", digits, phoneMap, result)
        return result
    }

    private fun backtrack(
        combination: String,
        nextDigits: String,
        phoneMap: Map<Char, List<String>>,
        result: MutableList<String>
    ) {
        if (nextDigits.isEmpty()) {
            result.add(combination)
        } else {
            val digit = nextDigits[0]
            val letters = phoneMap[digit] ?: listOf()
            for (letter in letters) {
                backtrack(combination + letter, nextDigits.substring(1), phoneMap, result)
            }
        }
    }
}
```

### Swift

```swift
class Solution {
    func letterCombinations(_ digits: String) -> [String] {
        if digits.isEmpty { return [] }

        let phoneMap: [Character: [String]] = [
            '2': ["a", "b", "c"],
            '3': ["d", "e", "f"],
            '4': ["g", "h", "i"],
            '5': ["j", "k", "l"],
            '6': ["m", "n", "o"],
            '7': ["p", "q", "r", "s"],
            '8': ["t", "u", "v"],
            '9': ["w", "x", "y", "z"]
        ]

        var result: [String] = []

        func backtrack(_ combination: String, _ nextDigits: String) {
            if nextDigits.isEmpty {
                result.append(combination)
            } else {
                let digit = nextDigits.first!
                let letters = phoneMap[digit] ?? []
                for letter in letters {
                    backtrack(combination + letter, String(nextDigits.dropFirst()))
                }
            }
        }

        backtrack("", digits)
        return result
    }
}
```


### The End

