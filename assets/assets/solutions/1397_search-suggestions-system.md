# Search Suggestions System

## Problem Statement

Given an array of strings `products` and a string `searchWord`, design a system that suggests at most three product names from `products` after each character of `searchWord` is typed. Suggested products should have a common prefix with `searchWord`. If there are more than three products with a common prefix, return the three lexicographically minimum products.

## Input

```text
products = ["mobile","mouse","moneypot","monitor","mousepad"]
searchWord = "mouse"
```

## Output

```text
[
    ["mobile","moneypot","monitor"],
    ["mobile","moneypot","monitor"],
    ["mouse","mousepad"],
    ["mouse","mousepad"],
    ["mouse","mousepad"]
]
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun suggestedProducts(products: Array<String>, searchWord: String): List<List<String>> {
        val result = mutableListOf<List<String>>()
        products.sort()
        val prefix = StringBuilder()

        for (char in searchWord) {
            prefix.append(char)
            val suggestions = mutableListOf<String>()
            for (product in products) {
                if (product.startsWith(prefix) && suggestions.size < 3) {
                    suggestions.add(product)
                }
            }
            result.add(suggestions)
        }

        return result
    }
}
```

### Dart

```dart
List<List<String>> suggestedProducts(List<String> products, String searchWord) {
  products.sort();
  List<List<String>> result = [];
  String prefix = "";

  for (var char in searchWord.split('')) {
    prefix += char;
    List<String> suggestions = [];
    for (var product in products) {
      if (product.startsWith(prefix)) {
        suggestions.add(product);
        if (suggestions.length == 3) break;
      }
    }
    result.add(suggestions);
  }

  return result;
}
```

### C#

```csharp
using System.Collections.Generic;
using System.Linq;

public class Solution {
    public IList<IList<string>> SuggestedProducts(string[] products, string searchWord) {
        Array.Sort(products);
        var result = new List<IList<string>>();
        var prefix = "";

        foreach (var c in searchWord) {
            prefix += c;
            var suggestions = new List<string>();
            foreach (var product in products) {
                if (product.StartsWith(prefix)) {
                    suggestions.Add(product);
                    if (suggestions.Count == 3) break;
                }
            }
            result.Add(suggestions);
        }

        return result;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public List<List<String>> suggestedProducts(String[] products, String searchWord) {
        Arrays.sort(products);
        List<List<String>> result = new ArrayList<>();
        StringBuilder prefix = new StringBuilder();

        for (char c : searchWord.toCharArray()) {
            prefix.append(c);
            List<String> suggestions = new ArrayList<>();
            for (String product : products) {
                if (product.startsWith(prefix.toString())) {
                    suggestions.add(product);
                    if (suggestions.size() == 3) break;
                }
            }
            result.add(suggestions);
        }

        return result;
    }
}
```

### Swift

```swift
class Solution {
    func suggestedProducts(_ products: [String], _ searchWord: String) -> [[String]] {
        let sortedProducts = products.sorted()
        var result = [[String]]()
        var prefix = ""

        for char in searchWord {
            prefix.append(char)
            var suggestions = [String]()
            for product in sortedProducts {
                if product.hasPrefix(prefix) {
                    suggestions.append(product)
                    if suggestions.count == 3 { break }
                }
            }
            result.append(suggestions)
        }

        return result
    }
}
```

### The End