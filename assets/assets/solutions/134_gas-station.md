# Gas Station

## Problem Statement

There are `n` gas stations along a circular route, where the amount of gas at the `i`th station is `gas[i]`. You have a car with an unlimited gas tank and it costs `cost[i]` of gas to travel from the `i`th station to its next `(i + 1)`th station. You begin the journey with an empty tank at one of the gas stations.

Given two integer arrays `gas` and `cost`, return the **starting gas station's index** if you can travel around the circuit once in the clockwise direction, otherwise return `-1`.

---

## Input

```text
gas = [1, 2, 3, 4, 5]
cost = [3, 4, 5, 1, 2]
```

## Output

```text
3
```


## Solutions

### Dart

```dart
int canCompleteCircuit(List<int> gas, List<int> cost) {
  int totalGas = 0, totalCost = 0, tank = 0, start = 0;
  for (int i = 0; i < gas.length; i++) {
    totalGas += gas[i];
    totalCost += cost[i];
    tank += gas[i] - cost[i];
    if (tank < 0) {
      tank = 0;
      start = i + 1;
    }
  }
  return totalGas < totalCost ? -1 : start % gas.length;
}
```


### C#

```csharp
public class Solution {
    public int CanCompleteCircuit(int[] gas, int[] cost) {
        int totalGas = 0, totalCost = 0, tank = 0, start = 0;
        for (int i = 0; i < gas.Length; i++) {
            totalGas += gas[i];
            totalCost += cost[i];
            tank += gas[i] - cost[i];
            if (tank < 0) {
                tank = 0;
                start = i + 1;
            }
        }
        return totalGas < totalCost ? -1 : start % gas.Length;
    }
}
```


### Java

```java
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int totalGas = 0, totalCost = 0, tank = 0, start = 0;
        for (int i = 0; i < gas.length; i++) {
            totalGas += gas[i];
            totalCost += cost[i];
            tank += gas[i] - cost[i];
            if (tank < 0) {
                tank = 0;
                start = i + 1;
            }
        }
        return totalGas < totalCost ? -1 : start % gas.length;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun canCompleteCircuit(gas: IntArray, cost: IntArray): Int {
        val n = gas.size
        var totalGas = 0
        var totalCost = 0
        var tank = 0
        var start = 0

        for (i in 0 until n) {
            totalGas += gas[i]
            totalCost += cost[i]
            tank += gas[i] - cost[i]
            if (tank < 0) {
                tank = 0
                start = i + 1
            }
        }

        return if (totalGas < totalCost) -1 else start % n
    }
}
```


### Swift

```swift
class Solution {
    func canCompleteCircuit(_ gas: [Int], _ cost: [Int]) -> Int {
        var totalGas = 0, totalCost = 0, tank = 0, start = 0
        for i in 0..<gas.count {
            totalGas += gas[i]
            totalCost += cost[i]
            tank += gas[i] - cost[i]
            if tank < 0 {
                tank = 0
                start = i + 1
            }
        }
        return totalGas < totalCost ? -1 : start % gas.count
    }
}
```


### The End

