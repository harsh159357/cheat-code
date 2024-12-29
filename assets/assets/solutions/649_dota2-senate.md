# Dota2 Senate

## Problem Statement

In the world of Dota2, there are two parties: the Radiant and the Dire. The Senate consists of senators from both parties. Each senator can make one decision:
1. Ban one senator's right to cast votes.
2. Announce the victory if all senators of the opposing party have lost their rights to vote.

Given a string `senate`, where `senate[i]` represents a senator from the `Radiant` (`'R'`) or `Dire` (`'D'`) party, determine which party will finally announce the victory.

## Input

```text
senate = "RDD"
```

## Output

```text
"Dire"
```

## Solutions

### Kotlin

```kotlin
import java.util.LinkedList

class Solution {
    fun predictPartyVictory(senate: String): String {
        val radiant = LinkedList<Int>()
        val dire = LinkedList<Int>()
        val n = senate.length

        for (i in senate.indices) {
            if (senate[i] == 'R') radiant.offer(i)
            else dire.offer(i)
        }

        while (radiant.isNotEmpty() && dire.isNotEmpty()) {
            val r = radiant.poll()
            val d = dire.poll()
            if (r < d) radiant.offer(r + n)
            else dire.offer(d + n)
        }

        return if (radiant.isNotEmpty()) "Radiant" else "Dire"
    }
}

fun main() {
    val senate = "RDD"
    val solution = Solution()
    println("Winning party: ${solution.predictPartyVictory(senate)}") // Output: "Dire"
}
```


### Dart

```dart
String predictPartyVictory(String senate) {
  Queue<int> radiant = Queue();
  Queue<int> dire = Queue();
  int n = senate.length;

  for (int i = 0; i < n; i++) {
    if (senate[i] == 'R') {
      radiant.add(i);
    } else {
      dire.add(i);
    }
  }

  while (radiant.isNotEmpty && dire.isNotEmpty) {
    int r = radiant.removeFirst();
    int d = dire.removeFirst();
    if (r < d) {
      radiant.add(r + n);
    } else {
      dire.add(d + n);
    }
  }

  return radiant.isNotEmpty ? "Radiant" : "Dire";
}

void main() {
  String senate = "RDD";
  print("Winning party: ${predictPartyVictory(senate)}"); // Output: "Dire"
}
```


### C#

```csharp
using System.Collections.Generic;

public class Solution {
    public string PredictPartyVictory(string senate) {
        Queue<int> radiant = new Queue<int>();
        Queue<int> dire = new Queue<int>();
        int n = senate.Length;

        for (int i = 0; i < n; i++) {
            if (senate[i] == 'R') radiant.Enqueue(i);
            else dire.Enqueue(i);
        }

        while (radiant.Count > 0 && dire.Count > 0) {
            int r = radiant.Dequeue();
            int d = dire.Dequeue();
            if (r < d) radiant.Enqueue(r + n);
            else dire.Enqueue(d + n);
        }

        return radiant.Count > 0 ? "Radiant" : "Dire";
    }
}
```


### Java

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public String predictPartyVictory(String senate) {
        Queue<Integer> radiant = new LinkedList<>();
        Queue<Integer> dire = new LinkedList<>();
        int n = senate.length();

        for (int i = 0; i < n; i++) {
            if (senate.charAt(i) == 'R') radiant.add(i);
            else dire.add(i);
        }

        while (!radiant.isEmpty() && !dire.isEmpty()) {
            int r = radiant.poll();
            int d = dire.poll();
            if (r < d) radiant.add(r + n);
            else dire.add(d + n);
        }

        return radiant.isEmpty() ? "Dire" : "Radiant";
    }
}
```


### Swift

```swift
class Solution {
    func predictPartyVictory(_ senate: String) -> String {
        var radiant = [Int]()
        var dire = [Int]()
        let n = senate.count
        let chars = Array(senate)

        for (i, c) in chars.enumerated() {
            if c == "R" {
                radiant.append(i)
            } else {
                dire.append(i)
            }
        }

        while !radiant.isEmpty && !dire.isEmpty {
            let r = radiant.removeFirst()
            let d = dire.removeFirst()
            if r < d {
                radiant.append(r + n)
            } else {
                dire.append(d + n)
            }
        }

        return radiant.isEmpty ? "Dire" : "Radiant"
    }
}

// Example usage
let senate = "RDD"
let solution = Solution()
print("Winning party: \(solution.predictPartyVictory(senate))") // Output: "Dire"
```

### The End