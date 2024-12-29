# Random Pick with Weight

## Problem Statement

You are given an array of positive integers `w` where `w[i]` describes the weight of the `i-th` index (0-based).  
Implement the `Solution` class:
1. `Solution(int[] w)` Initializes the object with the array `w`.
2. `int pickIndex()` Returns a random index such that the probability of picking index `i` is proportional to `w[i]`.

## Input

```text
w = [1, 3]
```

## Output

```text
0 (with probability 1/4) or 1 (with probability 3/4)
```

---

## Solutions

### Kotlin

```kotlin
import kotlin.random.Random

class Solution(w: IntArray) {
    private val prefixSums: IntArray

    init {
        prefixSums = IntArray(w.size)
        prefixSums[0] = w[0]
        for (i in 1 until w.size) {
            prefixSums[i] = prefixSums[i - 1] + w[i]
        }
    }

    fun pickIndex(): Int {
        val target = Random.nextInt(prefixSums.last()) + 1
        var left = 0
        var right = prefixSums.size - 1

        while (left < right) {
            val mid = left + (right - left) / 2
            if (prefixSums[mid] < target) {
                left = mid + 1
            } else {
                right = mid
            }
        }
        return left
    }
}

fun main() {
    val weights = intArrayOf(1, 3)
    val obj = Solution(weights)
    println(obj.pickIndex()) // Output: Either 0 or 1 with probabilities 1/4 and 3/4 respectively
}
```


### Dart

```dart
import 'dart:math';

class Solution {
  final List<int> prefixSums;

  Solution(List<int> w)
      : prefixSums = List<int>.generate(w.length, (i) => 0) {
    prefixSums[0] = w[0];
    for (int i = 1; i < w.length; i++) {
      prefixSums[i] = prefixSums[i - 1] + w[i];
    }
  }

  int pickIndex() {
    int target = Random().nextInt(prefixSums.last) + 1;
    int left = 0;
    int right = prefixSums.length - 1;

    while (left < right) {
      int mid = left + (right - left) ~/ 2;
      if (prefixSums[mid] < target) {
        left = mid + 1;
      } else {
        right = mid;
      }
    }
    return left;
  }
}

void main() {
  var weights = [1, 3];
  var obj = Solution(weights);
  print(obj.pickIndex()); // Output: Either 0 or 1 with probabilities 1/4 and 3/4 respectively
}
```

### C#

```csharp
using System;

public class Solution {
    private int[] prefixSums;
    private Random random;

    public Solution(int[] w) {
        prefixSums = new int[w.Length];
        prefixSums[0] = w[0];
        for (int i = 1; i < w.Length; i++) {
            prefixSums[i] = prefixSums[i - 1] + w[i];
        }
        random = new Random();
    }

    public int PickIndex() {
        int target = random.Next(1, prefixSums[^1] + 1);
        int left = 0, right = prefixSums.Length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (prefixSums[mid] < target) {
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
import java.util.Random;

class Solution {
    private int[] prefixSums;
    private Random random;

    public Solution(int[] w) {
        prefixSums = new int[w.length];
        prefixSums[0] = w[0];
        for (int i = 1; i < w.length; i++) {
            prefixSums[i] = prefixSums[i - 1] + w[i];
        }
        random = new Random();
    }

    public int pickIndex() {
        int target = random.nextInt(prefixSums[prefixSums.length - 1]) + 1;
        int left = 0, right = prefixSums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (prefixSums[mid] < target) {
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
import Foundation

class Solution {
    private var prefixSums: [Int]

    init(_ w: [Int]) {
        prefixSums = Array(repeating: 0, count: w.count)
        prefixSums[0] = w[0]
        for i in 1..<w.count {
            prefixSums[i] = prefixSums[i - 1] + w[i]
        }
    }

    func pickIndex() -> Int {
        let target = Int.random(in: 1...prefixSums.last!)
        var left = 0
        var right = prefixSums.count - 1

        while left < right {
            let mid = left + (right - left) / 2
            if prefixSums[mid] < target {
                left = mid + 1
            } else {
                right = mid
            }
        }
        return left
    }
}

let weights = [1, 3]
let obj = Solution(weights)
print(obj.pickIndex()) // Output: Either 0 or 1 with probabilities 1/4 and 3/4 respectively
```


### The End