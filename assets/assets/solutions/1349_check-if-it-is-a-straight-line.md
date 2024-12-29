# Check If It Is a Straight Line

## Problem Statement

You are given an array `coordinates`, where `coordinates[i] = [x, y]` represents the coordinates of a point on a 2D plane. Determine if these points make a straight line in the XY-plane.

## Input

```text
coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun checkStraightLine(coordinates: Array<IntArray>): Boolean {
        if (coordinates.size <= 2) return true

        val x0 = coordinates[0][0]
        val y0 = coordinates[0][1]
        val x1 = coordinates[1][0]
        val y1 = coordinates[1][1]

        val dx = x1 - x0
        val dy = y1 - y0

        for (i in 2 until coordinates.size) {
            val xi = coordinates[i][0]
            val yi = coordinates[i][1]
            if ((yi - y0) * dx != (xi - x0) * dy) {
                return false
            }
        }

        return true
    }
}
```

### Dart

```dart
bool checkStraightLine(List<List<int>> coordinates) {
  if (coordinates.length <= 2) return true;

  int x0 = coordinates[0][0], y0 = coordinates[0][1];
  int x1 = coordinates[1][0], y1 = coordinates[1][1];

  int dx = x1 - x0;
  int dy = y1 - y0;

  for (int i = 2; i < coordinates.length; i++) {
    int xi = coordinates[i][0], yi = coordinates[i][1];
    if ((yi - y0) * dx != (xi - x0) * dy) {
      return false;
    }
  }

  return true;
}
```

### C#

```csharp
public class Solution {
    public bool CheckStraightLine(int[][] coordinates) {
        if (coordinates.Length <= 2) return true;

        int x0 = coordinates[0][0], y0 = coordinates[0][1];
        int x1 = coordinates[1][0], y1 = coordinates[1][1];

        int dx = x1 - x0, dy = y1 - y0;

        for (int i = 2; i < coordinates.Length; i++) {
            int xi = coordinates[i][0], yi = coordinates[i][1];
            if ((yi - y0) * dx != (xi - x0) * dy) {
                return false;
            }
        }

        return true;
    }
}
```

### Java

```java
class Solution {
    public boolean checkStraightLine(int[][] coordinates) {
        if (coordinates.length <= 2) return true;

        int x0 = coordinates[0][0], y0 = coordinates[0][1];
        int x1 = coordinates[1][0], y1 = coordinates[1][1];

        int dx = x1 - x0, dy = y1 - y0;

        for (int i = 2; i < coordinates.length; i++) {
            int xi = coordinates[i][0], yi = coordinates[i][1];
            if ((yi - y0) * dx != (xi - x0) * dy) {
                return false;
            }
        }

        return true;
    }
}
```

### Swift

```swift
class Solution {
    func checkStraightLine(_ coordinates: [[Int]]) -> Bool {
        if coordinates.count <= 2 { return true }

        let x0 = coordinates[0][0], y0 = coordinates[0][1]
        let x1 = coordinates[1][0], y1 = coordinates[1][1]

        let dx = x1 - x0
        let dy = y1 - y0

        for i in 2..<coordinates.count {
            let xi = coordinates[i][0], yi = coordinates[i][1]
            if (yi - y0) * dx != (xi - x0) * dy {
                return false
            }
        }

        return true
    }
}
```

### The End