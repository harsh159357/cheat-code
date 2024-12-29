# Koko Eating Bananas

## Problem Statement

Koko loves to eat bananas. There are `n` piles of bananas, where the `i-th` pile has `piles[i]` bananas. The guards have gone and will return in `h` hours.

Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and moves on to the next pile.

Return the minimum integer `k` such that she can eat all the bananas within `h` hours.

## Input

```text
piles = [3, 6, 7, 11]
h = 8
```

## Output

```text
4
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun minEatingSpeed(piles: IntArray, h: Int): Int {
        var left = 1
        var right = piles.maxOrNull() ?: 0
        
        while (left < right) {
            val mid = left + (right - left) / 2
            var hours = 0
            
            for (pile in piles) {
                hours += (pile + mid - 1) / mid
            }
            
            if (hours > h) {
                left = mid + 1
            } else {
                right = mid
            }
        }
        
        return left
    }
}
```

### Dart

```dart
int minEatingSpeed(List<int> piles, int h) {
  int left = 1;
  int right = piles.reduce((a, b) => a > b ? a : b);

  while (left < right) {
    int mid = left + (right - left) ~/ 2;
    int hours = 0;

    for (int pile in piles) {
      hours += (pile + mid - 1) ~/ mid;
    }

    if (hours > h) {
      left = mid + 1;
    } else {
      right = mid;
    }
  }

  return left;
}
```

### C#

```csharp
using System;
using System.Linq;

public class Solution {
    public int MinEatingSpeed(int[] piles, int h) {
        int left = 1;
        int right = piles.Max();
        
        while (left < right) {
            int mid = left + (right - left) / 2;
            int hours = 0;
            
            foreach (int pile in piles) {
                hours += (pile + mid - 1) / mid;
            }
            
            if (hours > h) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        
        return left;
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int left = 1;
        int right = Arrays.stream(piles).max().getAsInt();
        
        while (left < right) {
            int mid = left + (right - left) / 2;
            int hours = 0;
            
            for (int pile : piles) {
                hours += (pile + mid - 1) / mid;
            }
            
            if (hours > h) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        
        return left;
    }
}
```

### Swift

```swift
class Solution {
    func minEatingSpeed(_ piles: [Int], _ h: Int) -> Int {
        var left = 1
        var right = piles.max() ?? 0
        
        while left < right {
            let mid = left + (right - left) / 2
            var hours = 0
            
            for pile in piles {
                hours += (pile + mid - 1) / mid
            }
            
            if hours > h {
                left = mid + 1
            } else {
                right = mid
            }
        }
        
        return left
    }
}
```

### The End