# Can Place Flowers

## Problem Statement

You have a long flowerbed in which some plots are planted, and some are not. However, flowers cannot be planted in adjacent plots. Given an integer array `flowerbed` containing `0`'s and `1`'s, where `0` means empty and `1` means not empty, and an integer `n`, return `true` if `n` new flowers can be planted without violating the no-adjacent-flowers rule, and `false` otherwise.

## Input

```text
flowerbed = [1, 0, 0, 0, 1], n = 1
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun canPlaceFlowers(flowerbed: IntArray, n: Int): Boolean {
        var count = 0
        var i = 0
        while (i < flowerbed.size) {
            if (flowerbed[i] == 0 && 
                (i == 0 || flowerbed[i - 1] == 0) && 
                (i == flowerbed.size - 1 || flowerbed[i + 1] == 0)) {
                flowerbed[i] = 1
                count++
            }
            i++
        }
        return count >= n
    }
}

fun main() {
    val solution = Solution()
    println(solution.canPlaceFlowers(intArrayOf(1, 0, 0, 0, 1), 1)) // Output: true
    println(solution.canPlaceFlowers(intArrayOf(1, 0, 0, 0, 1), 2)) // Output: false
}
```

### Dart

```dart
bool canPlaceFlowers(List<int> flowerbed, int n) {
  int count = 0;
  int i = 0;

  while (i < flowerbed.length) {
    if (flowerbed[i] == 0 && 
        (i == 0 || flowerbed[i - 1] == 0) && 
        (i == flowerbed.length - 1 || flowerbed[i + 1] == 0)) {
      flowerbed[i] = 1;
      count++;
    }
    i++;
  }

  return count >= n;
}

void main() {
  print(canPlaceFlowers([1, 0, 0, 0, 1], 1)); // Output: true
  print(canPlaceFlowers([1, 0, 0, 0, 1], 2)); // Output: false
}
```

### C#

```csharp
public class Solution {
    public bool CanPlaceFlowers(int[] flowerbed, int n) {
        int count = 0;
        for (int i = 0; i < flowerbed.Length; i++) {
            if (flowerbed[i] == 0 && 
                (i == 0 || flowerbed[i - 1] == 0) && 
                (i == flowerbed.Length - 1 || flowerbed[i + 1] == 0)) {
                flowerbed[i] = 1;
                count++;
            }
        }
        return count >= n;
    }
}
```

### Java

```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int count = 0;
        for (int i = 0; i < flowerbed.length; i++) {
            if (flowerbed[i] == 0 && 
                (i == 0 || flowerbed[i - 1] == 0) && 
                (i == flowerbed.length - 1 || flowerbed[i + 1] == 0)) {
                flowerbed[i] = 1;
                count++;
            }
        }
        return count >= n;
    }
}
```

### Swift

```swift
class Solution {
    func canPlaceFlowers(_ flowerbed: [Int], _ n: Int) -> Bool {
        var flowerbed = flowerbed
        var count = 0
        var i = 0

        while i < flowerbed.count {
            if flowerbed[i] == 0 &&
               (i == 0 || flowerbed[i - 1] == 0) &&
               (i == flowerbed.count - 1 || flowerbed[i + 1] == 0) {
                flowerbed[i] = 1
                count += 1
            }
            i += 1
        }

        return count >= n
    }
}

// Example usage
let solution = Solution()
print(solution.canPlaceFlowers([1, 0, 0, 0, 1], 1)) // Output: true
print(solution.canPlaceFlowers([1, 0, 0, 0, 1], 2)) // Output: false
```

### The End