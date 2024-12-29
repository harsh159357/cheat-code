# Successful Pairs of Spells and Potions

## Problem Statement

You are given two arrays: `spells` and `potions`, both of size `n` and `m` respectively. You are also given an integer `success`.

A spell and potion pair is considered **successful** if their product is greater than or equal to `success`.

Return an array of length `n` where each element is the number of successful pairs with the corresponding spell.

## Input

```text
spells = [10, 2, 3]
potions = [1, 2, 3, 4]
success = 8
```

## Output

```text
[4, 2, 2]
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun successfulPairs(spellsInput: IntArray, potionsInput: IntArray, success: Long): IntArray {
        val map = mutableMapOf<Int, Int>()
        val spells = spellsInput.sorted()
        val potions = potionsInput.sortedDescending()
        var lastIndex = 0
        var totalPairsTillNow = 0

        for (spell in spells) {
            var existingPairs = totalPairsTillNow
            var extraPair = 0
            var j = lastIndex

            while (j < potions.size) {
                val potion = potions[j]
                if (spell.toLong() * potion >= success) {
                    totalPairsTillNow++
                    extraPair++
                } else {
                    lastIndex = j
                    break
                }
                j++
            }

            if (j == potions.size) {
                lastIndex = j
            }
            map[spell] = existingPairs + extraPair
        }

        return spellsInput.map { map[it] ?: 0 }.toIntArray()
    }
}

fun main() {
    val spells = intArrayOf(10, 2, 3)
    val potions = intArrayOf(1, 2, 3, 4)
    val success = 8L
    println(Solution().successfulPairs(spells, potions, success).toList()) // Output: [4, 2, 2]
}
```

### Dart

```dart
List<int> successfulPairs(List<int> spells, List<int> potions, int success) {
  Map<int, int> map = {};
  List<int> sortedSpells = List.from(spells)..sort();
  List<int> sortedPotions = List.from(potions)..sort((a, b) => b.compareTo(a));
  int lastIndex = 0;
  int totalPairsTillNow = 0;

  for (int spell in sortedSpells) {
    int existingPairs = totalPairsTillNow;
    int extraPair = 0;
    int j = lastIndex;

    while (j < sortedPotions.length) {
      int potion = sortedPotions[j];
      if (spell * potion >= success) {
        totalPairsTillNow++;
        extraPair++;
      } else {
        lastIndex = j;
        break;
      }
      j++;
    }

    if (j == sortedPotions.length) {
      lastIndex = j;
    }
    map[spell] = existingPairs + extraPair;
  }

  return spells.map((spell) => map[spell] ?? 0).toList();
}

void main() {
  List<int> spells = [10, 2, 3];
  List<int> potions = [1, 2, 3, 4];
  int success = 8;
  print(successfulPairs(spells, potions, success)); // Output: [4, 2, 2]
}
```

### C#

```csharp
public class Solution {
    public int[] SuccessfulPairs(int[] spells, int[] potions, long success) {
        var map = new Dictionary<int, int>();
        var sortedSpells = spells.OrderBy(x => x).ToArray();
        var sortedPotions = potions.OrderByDescending(x => x).ToArray();
        int lastIndex = 0, totalPairsTillNow = 0;

        foreach (int spell in sortedSpells) {
            int existingPairs = totalPairsTillNow, extraPair = 0, j = lastIndex;

            while (j < sortedPotions.Length) {
                int potion = sortedPotions[j];
                if ((long)spell * potion >= success) {
                    totalPairsTillNow++;
                    extraPair++;
                } else {
                    lastIndex = j;
                    break;
                }
                j++;
            }

            if (j == sortedPotions.Length) {
                lastIndex = j;
            }
            map[spell] = existingPairs + extraPair;
        }

        return spells.Select(spell => map[spell]).ToArray();
    }
}
```

### Java

```java
import java.util.*;

class Solution {
    public int[] successfulPairs(int[] spells, int[] potions, long success) {
        Map<Integer, Integer> map = new HashMap<>();
        int[] sortedSpells = Arrays.stream(spells).sorted().toArray();
        Arrays.sort(potions);
        int lastIndex = 0, totalPairsTillNow = 0;

        for (int spell : sortedSpells) {
            int existingPairs = totalPairsTillNow, extraPair = 0, j = lastIndex;

            while (j < potions.length) {
                int potion = potions[potions.length - 1 - j];
                if ((long)spell * potion >= success) {
                    totalPairsTillNow++;
                    extraPair++;
                } else {
                    lastIndex = j;
                    break;
                }
                j++;
            }

            if (j == potions.length) {
                lastIndex = j;
            }
            map.put(spell, existingPairs + extraPair);
        }

        return Arrays.stream(spells).map(spell -> map.get(spell)).toArray();
    }
}
```

### The End