# Kids With the Greatest Number of Candies

## Problem Statement

Given the array `candies` representing the number of candies each child has and an integer `extraCandies`, return a boolean array where each element is `true` if, after giving the child the `extraCandies`, they have the greatest number of candies among all children, or `false` otherwise.

## Input

```text
candies = [2,3,5,1,3]
extraCandies = 3
```

## Output

```text
[true, true, true, false, true]
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun kidsWithCandies(candies: IntArray, extraCandies: Int): BooleanArray {
        val result = BooleanArray(candies.size)
        val maxCandies = candies.maxOrNull() ?: 0

        for (i in candies.indices) {
            result[i] = candies[i] + extraCandies >= maxCandies
        }

        return result
    }
}
```

### Dart

```dart
List<bool> kidsWithCandies(List<int> candies, int extraCandies) {
  int maxCandies = candies.reduce((a, b) => a > b ? a : b);
  return candies.map((candy) => candy + extraCandies >= maxCandies).toList();
}
```

### C#

```csharp
public class Solution {
    public IList<bool> KidsWithCandies(int[] candies, int extraCandies) {
        int maxCandies = candies.Max();
        List<bool> result = new List<bool>();

        foreach (int candy in candies) {
            result.Add(candy + extraCandies >= maxCandies);
        }

        return result;
    }
}
```

### Java

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int maxCandies = 0;
        for (int candy : candies) {
            maxCandies = Math.max(maxCandies, candy);
        }

        List<Boolean> result = new ArrayList<>();
        for (int candy : candies) {
            result.add(candy + extraCandies >= maxCandies);
        }

        return result;
    }
}
```

### Swift

```swift
class Solution {
    func kidsWithCandies(_ candies: [Int], _ extraCandies: Int) -> [Bool] {
        let maxCandies = candies.max() ?? 0
        return candies.map { $0 + extraCandies >= maxCandies }
    }
}
```

### The End