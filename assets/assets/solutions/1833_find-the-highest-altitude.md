# Find the Highest Altitude

## Problem Statement

There is a biker going on a road trip. The road trip consists of `n + 1` points at different altitudes. The biker starts at point `0` with an altitude of `0`.

You are given an integer array `gain` of length `n` where `gain[i]` is the net gain in altitude between points `i` and `i + 1` for all `(0 <= i < n)`. Return the **highest altitude** of a point.

## Input

```text
gain = [-5,1,5,0,-7]
```

## Output

```text
1
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun largestAltitude(gain: IntArray): Int {
        var maxAltitude = 0
        var currentAltitude = 0
        for (altitude in gain) {
            currentAltitude += altitude
            maxAltitude = maxOf(maxAltitude, currentAltitude)
        }
        return maxAltitude
    }
}

fun main() {
    val gain = intArrayOf(-5, 1, 5, 0, -7)
    println(Solution().largestAltitude(gain)) // Output: 1
}
```

### Dart

```dart
int largestAltitude(List<int> gain) {
  int maxAltitude = 0;
  int currentAltitude = 0;

  for (int altitude in gain) {
    currentAltitude += altitude;
    maxAltitude = max(maxAltitude, currentAltitude);
  }

  return maxAltitude;
}

void main() {
  List<int> gain = [-5, 1, 5, 0, -7];
  print(largestAltitude(gain)); // Output: 1
}
```

### C#

```csharp
public class Solution {
    public int LargestAltitude(int[] gain) {
        int maxAltitude = 0;
        int currentAltitude = 0;

        foreach (int altitude in gain) {
            currentAltitude += altitude;
            maxAltitude = Math.Max(maxAltitude, currentAltitude);
        }

        return maxAltitude;
    }
}
```

### Java

```java
class Solution {
    public int largestAltitude(int[] gain) {
        int maxAltitude = 0;
        int currentAltitude = 0;

        for (int altitude : gain) {
            currentAltitude += altitude;
            maxAltitude = Math.max(maxAltitude, currentAltitude);
        }

        return maxAltitude;
    }
}
```

### Swift

```swift
class Solution {
    func largestAltitude(_ gain: [Int]) -> Int {
        var maxAltitude = 0
        var currentAltitude = 0

        for altitude in gain {
            currentAltitude += altitude
            maxAltitude = max(maxAltitude, currentAltitude)
        }

        return maxAltitude
    }
}

let gain = [-5, 1, 5, 0, -7]
print(Solution().largestAltitude(gain)) // Output: 1
```

### The End