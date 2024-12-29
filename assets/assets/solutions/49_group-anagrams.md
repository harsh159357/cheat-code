# Group Anagrams

## Problem Statement

Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Input

```text
strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
```

## Output

```text
[["bat"], ["nat", "tan"], ["ate", "eat", "tea"]]  
(Explanation: These are the groups of anagrams in the array.)
```


## Solutions

### Dart

```dart
List<List<String>> groupAnagrams(List<String> strs) {
  Map<String, List<String>> map = {};

  for (String str in strs) {
    List<String> chars = str.split('');
    chars.sort();
    String key = chars.join();
    map.putIfAbsent(key, () => []).add(str);
  }

  return map.values.toList();
}

void main() {
  print(groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"]));
  // Output: [["bat"], ["nat", "tan"], ["ate", "eat", "tea"]]
}
```

### C#

```csharp
public class Solution {
    public IList<IList<string>> GroupAnagrams(string[] strs) {
        Dictionary<string, List<string>> map = new Dictionary<string, List<string>>();

        foreach (string str in strs) {
            char[] chars = str.ToCharArray();
            Array.Sort(chars);
            string key = new string(chars);

            if (!map.ContainsKey(key)) {
                map[key] = new List<string>();
            }

            map[key].Add(str);
        }

        return new List<IList<string>>(map.Values);
    }
}
```

### Java

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();

        for (String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String key = new String(chars);

            map.putIfAbsent(key, new ArrayList<>());
            map.get(key).add(str);
        }

        return new ArrayList<>(map.values());
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun groupAnagrams(strs: Array<String>): List<List<String>> {
        val map = mutableMapOf<String, MutableList<String>>()

        for (str in strs) {
            val key = String(str.toCharArray().sortedArray())
            map.getOrPut(key) { mutableListOf() }.add(str)
        }

        return map.values.toList()
    }
}
```

### Swift

```swift
class Solution {
    func groupAnagrams(_ strs: [String]) -> [[String]] {
        var map = [String: [String]]()

        for str in strs {
            let key = String(str.sorted())
            map[key, default: []].append(str)
        }

        return Array(map.values)
    }
}

let solution = Solution()
print(solution.groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"]))
// Output: [["bat"], ["nat", "tan"], ["ate", "eat", "tea"]]
```


### The End

