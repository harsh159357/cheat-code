# Max Points on a Line

## Problem Statement

Given an array of `points` where `points[i] = [xi, yi]` represents a point on the 2D plane, return the maximum number of points that lie on the same straight line.

---

## Input

```text
points = [[1,1],[2,2],[3,3]]
```

---

## Output

```text
3
```


## Solutions

### Kotlin

```kotlin
class Solution {
    fun maxPoints(points: Array<IntArray>): Int {
        if (points.size <= 2) return points.size
        var maxPoints = 0

        for (i in points.indices) {
            val slopes = mutableMapOf<Double, Int>()
            var duplicatePoints = 1
            var verticalPoints = 0

            for (j in points.indices) {
                if (i != j) {
                    if (points[i][0] == points[j][0]) {
                        if (points[i][1] == points[j][1]) {
                            duplicatePoints++
                        } else {
                            verticalPoints++
                        }
                    } else {
                        val slope = (points[j][1] - points[i][1]).toDouble() / (points[j][0] - points[i][0])
                        slopes[slope] = slopes.getOrDefault(slope, 0) + 1
                    }
                }
            }

            var currentMax = verticalPoints
            for (count in slopes.values) {
                currentMax = maxOf(currentMax, count)
            }

            currentMax += duplicatePoints
            maxPoints = maxOf(maxPoints, currentMax)
        }

        return maxPoints
    }
}
```


### Dart

```dart
int maxPoints(List<List<int>> points) {
  if (points.length <= 2) return points.length;

  int maxPoints = 0;

  for (int i = 0; i < points.length; i++) {
    Map<double, int> slopes = {};
    int duplicatePoints = 1;
    int verticalPoints = 0;

    for (int j = 0; j < points.length; j++) {
      if (i != j) {
        if (points[i][0] == points[j][0]) {
          if (points[i][1] == points[j][1]) {
            duplicatePoints++;
          } else {
            verticalPoints++;
          }
        } else {
          double slope = (points[j][1] - points[i][1]) / (points[j][0] - points[i][0]);
          slopes[slope] = (slopes[slope] ?? 0) + 1;
        }
      }
    }

    int currentMax = verticalPoints;
    for (int count in slopes.values) {
      currentMax = currentMax > count ? currentMax : count;
    }

    currentMax += duplicatePoints;
    maxPoints = maxPoints > currentMax ? maxPoints : currentMax;
  }

  return maxPoints;
}
```


### C#

```csharp
public class Solution {
    public int MaxPoints(int[][] points) {
        if (points.Length <= 2) return points.Length;

        int maxPoints = 0;

        for (int i = 0; i < points.Length; i++) {
            Dictionary<double, int> slopes = new Dictionary<double, int>();
            int duplicatePoints = 1;
            int verticalPoints = 0;

            for (int j = 0; j < points.Length; j++) {
                if (i != j) {
                    if (points[i][0] == points[j][0]) {
                        if (points[i][1] == points[j][1]) {
                            duplicatePoints++;
                        } else {
                            verticalPoints++;
                        }
                    } else {
                        double slope = (double)(points[j][1] - points[i][1]) / (points[j][0] - points[i][0]);
                        if (!slopes.ContainsKey(slope)) slopes[slope] = 0;
                        slopes[slope]++;
                    }
                }
            }

            int currentMax = verticalPoints;
            foreach (var count in slopes.Values) {
                currentMax = Math.Max(currentMax, count);
            }

            currentMax += duplicatePoints;
            maxPoints = Math.Max(maxPoints, currentMax);
        }

        return maxPoints;
    }
}
```


### Swift

```swift
class Solution {
    func maxPoints(_ points: [[Int]]) -> Int {
        if points.count <= 2 { return points.count }
        var maxPoints = 0

        for i in 0..<points.count {
            var slopes = [Double: Int]()
            var duplicatePoints = 1
            var verticalPoints = 0

            for j in 0..<points.count {
                if i != j {
                    if points[i][0] == points[j][0] {
                        if points[i][1] == points[j][1] {
                            duplicatePoints += 1
                        } else {
                            verticalPoints += 1
                        }
                    } else {
                        let slope = Double(points[j][1] - points[i][1]) / Double(points[j][0] - points[i][0])
                        slopes[slope, default: 0] += 1
                    }
                }
            }

            var currentMax = verticalPoints
            for count in slopes.values {
                currentMax = max(currentMax, count)
            }

            currentMax += duplicatePoints
            maxPoints = max(maxPoints, currentMax)
        }

        return maxPoints
    }
}
```



### The End

