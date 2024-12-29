# Average Salary Excluding the Minimum and Maximum Salary

## Problem Statement

You are given an array `salary` where `salary[i]` is the salary of the `i-th` employee. Return the average salary of employees excluding the minimum and maximum salary.

## Input

```text
salary = [4000, 3000, 1000, 2000]
```

## Output

```text
2500.0
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun average(salary: IntArray): Double {
        val n = salary.size
        val sortedSalary = salary.sorted()
        var sum = 0

        for (i in 1 until n - 1) {
            sum += sortedSalary[i]
        }

        return sum.toDouble() / (n - 2)
    }
}
```

### Dart

```dart
double average(List<int> salary) {
  salary.sort();
  int sum = 0;

  for (int i = 1; i < salary.length - 1; i++) {
    sum += salary[i];
  }

  return sum / (salary.length - 2);
}
```

### C#

```csharp
public class Solution {
    public double Average(int[] salary) {
        Array.Sort(salary);
        int sum = 0;

        for (int i = 1; i < salary.Length - 1; i++) {
            sum += salary[i];
        }

        return (double)sum / (salary.Length - 2);
    }
}
```

### Java

```java
class Solution {
    public double average(int[] salary) {
        Arrays.sort(salary);
        int sum = 0;

        for (int i = 1; i < salary.length - 1; i++) {
            sum += salary[i];
        }

        return (double) sum / (salary.length - 2);
    }
}
```

### Swift

```swift
class Solution {
    func average(_ salary: [Int]) -> Double {
        let sortedSalary = salary.sorted()
        let sum = sortedSalary[1..<(salary.count - 1)].reduce(0, +)
        return Double(sum) / Double(salary.count - 2)
    }
}
```

### The End