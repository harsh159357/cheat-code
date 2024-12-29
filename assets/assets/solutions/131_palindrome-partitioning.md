# Palindrome Partitioning

## Problem Statement

Given a string `s`, partition `s` such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of `s`.

---

## Input

```text
s = "aab"
```

## Output

```text
[
  ["a", "a", "b"],
  ["aa", "b"]
]
```


## Solutions

### Dart

```dart
List<List<String>> partition(String s) {
  List<List<String>> result = [];
  List<String> currentPartition = [];

  bool isPalindrome(String s, int start, int end) {
    while (start < end) {
      if (s[start++] != s[end--]) return false;
    }
    return true;
  }

  void backtrack(int start) {
    if (start >= s.length) {
      result.add(List.from(currentPartition));
      return;
    }
    for (int end = start; end < s.length; end++) {
      if (isPalindrome(s, start, end)) {
        currentPartition.add(s.substring(start, end + 1));
        backtrack(end + 1);
        currentPartition.removeLast();
      }
    }
  }

  backtrack(0);
  return result;
}
```


### C#

```csharp
public class Solution {
    public IList<IList<string>> Partition(string s) {
        var result = new List<IList<string>>();
        var currentPartition = new List<string>();

        bool IsPalindrome(int start, int end) {
            while (start < end) {
                if (s[start++] != s[end--]) return false;
            }
            return true;
        }

        void Backtrack(int start) {
            if (start >= s.Length) {
                result.Add(new List<string>(currentPartition));
                return;
            }
            for (int end = start; end < s.Length; end++) {
                if (IsPalindrome(start, end)) {
                    currentPartition.Add(s.Substring(start, end - start + 1));
                    Backtrack(end + 1);
                    currentPartition.RemoveAt(currentPartition.Count - 1);
                }
            }
        }

        Backtrack(0);
        return result;
    }
}
```


### Java

```java
class Solution {
    public List<List<String>> partition(String s) {
        List<List<String>> result = new ArrayList<>();
        List<String> currentPartition = new ArrayList<>();

        boolean isPalindrome(String s, int start, int end) {
            while (start < end) {
                if (s.charAt(start++) != s.charAt(end--)) return false;
            }
            return true;
        }

        void backtrack(int start) {
            if (start >= s.length()) {
                result.add(new ArrayList<>(currentPartition));
                return;
            }
            for (int end = start; end < s.length(); end++) {
                if (isPalindrome(s, start, end)) {
                    currentPartition.add(s.substring(start, end + 1));
                    backtrack(end + 1);
                    currentPartition.remove(currentPartition.size() - 1);
                }
            }
        }

        backtrack(0);
        return result;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun partition(s: String): List<List<String>> {
        val result = mutableListOf<List<String>>()
        val currentPartition = mutableListOf<String>()

        fun isPalindrome(start: Int, end: Int): Boolean {
            var i = start
            var j = end
            while (i < j) {
                if (s[i++] != s[j--]) return false
            }
            return true
        }

        fun backtrack(start: Int) {
            if (start >= s.length) {
                result.add(ArrayList(currentPartition))
                return
            }
            for (end in start until s.length) {
                if (isPalindrome(start, end)) {
                    currentPartition.add(s.substring(start, end + 1))
                    backtrack(end + 1)
                    currentPartition.removeAt(currentPartition.size - 1)
                }
            }
        }

        backtrack(0)
        return result
    }
}
```


### Swift

```swift
class Solution {
    func partition(_ s: String) -> [[String]] {
        var result = [[String]]()
        var currentPartition = [String]()

        func isPalindrome(_ s: [Character], _ start: Int, _ end: Int) -> Bool {
            var i = start, j = end
            while i < j {
                if s[i] != s[j] { return false }
                i += 1
                j -= 1
            }
            return true
        }

        func backtrack(_ s: [Character], _ start: Int) {
            if start >= s.count {
                result.append(currentPartition)
                return
            }
            for end in start..<s.count {
                if isPalindrome(s, start, end) {
                    currentPartition.append(String(s[start...end]))
                    backtrack(s, end + 1)
                    currentPartition.removeLast()
                }
            }
        }

        backtrack(Array(s), 0)
        return result
    }
}
```


### The End

