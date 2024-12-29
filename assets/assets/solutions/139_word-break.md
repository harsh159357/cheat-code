# Word Break

## Problem Statement

Given a string `s` and a dictionary of strings `wordDict`, return `true` if `s` can be segmented into a space-separated sequence of one or more dictionary words.

## Input

```text
s = "leetcode"
wordDict = ["leet", "code"]
```

## Output

```text
true
```


## Solutions

### Dart

```dart
bool wordBreak(String s, List<String> wordDict) {
  final wordSet = Set<String>.from(wordDict);
  List<bool> dp = List.filled(s.length + 1, false);
  dp[0] = true;

  for (int i = 1; i <= s.length; i++) {
    for (int j = 0; j < i; j++) {
      if (dp[j] && wordSet.contains(s.substring(j, i))) {
        dp[i] = true;
        break;
      }
    }
  }
  return dp[s.length];
}
```


### C#

```csharp
public class Solution {
    public bool WordBreak(string s, IList<string> wordDict) {
        HashSet<string> wordSet = new HashSet<string>(wordDict);
        bool[] dp = new bool[s.Length + 1];
        dp[0] = true;

        for (int i = 1; i <= s.Length; i++) {
            for (int j = 0; j < i; j++) {
                if (dp[j] && wordSet.Contains(s.Substring(j, i - j))) {
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp[s.Length];
    }
}
```


### Java

```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        Set<String> wordSet = new HashSet<>(wordDict);
        boolean[] dp = new boolean[s.length() + 1];
        dp[0] = true;

        for (int i = 1; i <= s.length(); i++) {
            for (int j = 0; j < i; j++) {
                if (dp[j] && wordSet.contains(s.substring(j, i))) {
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp[s.length()];
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun wordBreak(s: String, wordDict: List<String>): Boolean {
        val wordSet = wordDict.toHashSet()
        val dp = BooleanArray(s.length + 1)
        dp[0] = true
        for (i in 1..s.length) {
            for (j in 0 until i) {
                if (dp[j] && wordSet.contains(s.substring(j, i))) {
                    dp[i] = true
                    break
                }
            }
        }
        return dp[s.length]
    }
}
```


### Swift

```swift
class Solution {
    func wordBreak(_ s: String, _ wordDict: [String]) -> Bool {
        let wordSet = Set(wordDict)
        var dp = [Bool](repeating: false, count: s.count + 1)
        dp[0] = true
        let sArray = Array(s)

        for i in 1...s.count {
            for j in 0..<i {
                let substring = String(sArray[j..<i])
                if dp[j] && wordSet.contains(substring) {
                    dp[i] = true
                    break
                }
            }
        }
        return dp[s.count]
    }
}
```


### The End

