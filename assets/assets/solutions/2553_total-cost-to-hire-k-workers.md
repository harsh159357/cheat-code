# Total Cost to Hire K Workers

## Problem Statement

You are given an array `costs` where `costs[i]` is the cost of hiring the `i-th` worker. You are also given two integers `k` and `candidates`.  
You need to hire exactly `k` workers using the following rules:

1. You can hire workers either from the beginning or the end of the array.
2. You need to minimize the total cost of hiring.

Return the minimum total cost to hire exactly `k` workers.

---

## Input

```text
costs = [17, 12, 10, 2, 7, 2, 11, 20]
k = 3
candidates = 4
```

## Output

```text
11
```

---

## Solutions

### Kotlin

```kotlin
import java.util.PriorityQueue

class Solution {
    fun totalCost(costs: IntArray, k: Int, candidates: Int): Long {
        val pq = PriorityQueue<IntArray> { cost1, cost2 ->
            if (cost1[0] == cost2[0]) cost1[1] - cost2[1] else cost1[0] - cost2[0]
        }

        var cost: Long = 0
        var startIndex = 0
        var endIndex = costs.size - 1
        var startMax = startIndex + candidates
        var endMax = endIndex - candidates

        for (i in 0 until k) {
            if (startMax <= endMax) {
                while (startIndex < startMax) {
                    pq.add(intArrayOf(costs[startIndex], startIndex))
                    startIndex++
                }
                while (endMax < endIndex) {
                    pq.add(intArrayOf(costs[endIndex], endIndex))
                    endIndex--
                }
            } else {
                while (startIndex <= endIndex) {
                    pq.add(intArrayOf(costs[startIndex], startIndex))
                    startIndex++
                }
            }

            val minValue = pq.poll()

            if (minValue[1] < startIndex) {
                startMax = startIndex + 1
            } else {
                endMax = endIndex - 1
            }

            cost += minValue[0]
        }
        return cost
    }
}
```


### Dart

```dart
import 'dart:collection';

int totalCost(List<int> costs, int k, int candidates) {
  var pq = PriorityQueue<List<int>>((cost1, cost2) {
    if (cost1[0] == cost2[0]) {
      return cost1[1] - cost2[1];
    }
    return cost1[0] - cost2[0];
  });

  int cost = 0;
  int startIndex = 0;
  int endIndex = costs.length - 1;
  int startMax = startIndex + candidates;
  int endMax = endIndex - candidates;

  for (int i = 0; i < k; i++) {
    if (startMax <= endMax) {
      while (startIndex < startMax) {
        pq.add([costs[startIndex], startIndex]);
        startIndex++;
      }
      while (endMax < endIndex) {
        pq.add([costs[endIndex], endIndex]);
        endIndex--;
      }
    } else {
      while (startIndex <= endIndex) {
        pq.add([costs[startIndex], startIndex]);
        startIndex++;
      }
    }

    List<int> minValue = pq.removeFirst();

    if (minValue[1] < startIndex) {
      startMax = startIndex + 1;
    } else {
      endMax = endIndex - 1;
    }

    cost += minValue[0];
  }
  return cost;
}
```


### C#

```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public long TotalCost(int[] costs, int k, int candidates) {
        var pq = new PriorityQueue<int[], int>(Comparer<int>.Create((x, y) => {
            if (x[0] == y[0]) return x[1] - y[1];
            return x[0] - y[0];
        }));

        long cost = 0;
        int startIndex = 0, endIndex = costs.Length - 1;
        int startMax = startIndex + candidates, endMax = endIndex - candidates;

        for (int i = 0; i < k; i++) {
            if (startMax <= endMax) {
                while (startIndex < startMax) {
                    pq.Enqueue(new[] { costs[startIndex], startIndex });
                    startIndex++;
                }
                while (endMax < endIndex) {
                    pq.Enqueue(new[] { costs[endIndex], endIndex });
                    endIndex--;
                }
            } else {
                while (startIndex <= endIndex) {
                    pq.Enqueue(new[] { costs[startIndex], startIndex });
                    startIndex++;
                }
            }

            var minValue = pq.Dequeue();

            if (minValue[1] < startIndex) {
                startMax = startIndex + 1;
            } else {
                endMax = endIndex - 1;
            }

            cost += minValue[0];
        }
        return cost;
    }
}
```


### Java

```java
import java.util.*;

class Solution {
    public long totalCost(int[] costs, int k, int candidates) {
        PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> {
            if (a[0] == b[0]) return a[1] - b[1];
            return a[0] - b[0];
        });

        long cost = 0;
        int startIndex = 0, endIndex = costs.length - 1;
        int startMax = startIndex + candidates, endMax = endIndex - candidates;

        for (int i = 0; i < k; i++) {
            if (startMax <= endMax) {
                while (startIndex < startMax) {
                    pq.add(new int[] { costs[startIndex], startIndex });
                    startIndex++;
                }
                while (endMax < endIndex) {
                    pq.add(new int[] { costs[endIndex], endIndex });
                    endIndex--;
                }
            } else {
                while (startIndex <= endIndex) {
                    pq.add(new int[] { costs[startIndex], startIndex });
                    startIndex++;
                }
            }

            int[] minValue = pq.poll();

            if (minValue[1] < startIndex) {
                startMax = startIndex + 1;
            } else {
                endMax = endIndex - 1;
            }

            cost += minValue[0];
        }
        return cost;
    }
}
```


### Swift

```swift
class Solution {
    func totalCost(_ costs: [Int], _ k: Int, _ candidates: Int) -> Int {
        var pq = PriorityQueue<(Int, Int)> { a, b in
            if a.0 == b.0 { return a.1 < b.1 }
            return a.0 < b.0
        }

        var cost = 0
        var startIndex = 0
        var endIndex = costs.count - 1
        var startMax = startIndex + candidates
        var endMax = endIndex - candidates

        for _ in 0..<k {
            if startMax <= endMax {
                while startIndex < startMax {
                    pq.enqueue((costs[startIndex], startIndex))
                    startIndex += 1
                }
                while endMax < endIndex {
                    pq.enqueue((costs[endIndex], endIndex))
                    endIndex -= 1
                }
            } else {
                while startIndex <= endIndex {
                    pq.enqueue((costs[startIndex], startIndex))
                    startIndex += 1
                }
            }

            let minValue = pq.dequeue()!

            if minValue.1 < startIndex {
                startMax = startIndex + 1
            } else {
                endMax = endIndex - 1
            }

            cost += minValue.0
        }
        return cost
    }
}
```

### The End

