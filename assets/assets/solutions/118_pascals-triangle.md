# Pascal's Triangle

## Problem Statement

Given an integer `numRows`, return the first `numRows` of Pascal's Triangle.

In Pascal's Triangle:
- Each number is the sum of the two numbers directly above it.

## Input

```text
numRows = 5
```

## Output

```text
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```


## Solutions

### Dart

```dart
List<List<int>> generate(int numRows) {
  List<List<int>> triangle = [];

  if (numRows == 0) return triangle;

  triangle.add([1]); // First row

  for (int i = 1; i < numRows; i++) {
    List<int> prevRow = triangle[i - 1];
    List<int> newRow = [1]; // First element of the row

    for (int j = 1; j < i; j++) {
      newRow.add(prevRow[j - 1] + prevRow[j]); // Middle elements
    }

    newRow.add(1); // Last element of the row
    triangle.add(newRow);
  }

  return triangle;
}
```


### C#

```csharp
public class Solution {
    public IList<IList<int>> Generate(int numRows) {
        var triangle = new List<IList<int>>();

        if (numRows == 0) return triangle;

        triangle.Add(new List<int> { 1 }); // First row

        for (int i = 1; i < numRows; i++) {
            var prevRow = triangle[i - 1];
            var newRow = new List<int> { 1 }; // First element of the row

            for (int j = 1; j < i; j++) {
                newRow.Add(prevRow[j - 1] + prevRow[j]); // Middle elements
            }

            newRow.Add(1); // Last element of the row
            triangle.Add(newRow);
        }

        return triangle;
    }
}
```


### Java

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> triangle = new ArrayList<>();

        if (numRows == 0) return triangle;

        triangle.add(new ArrayList<>());
        triangle.get(0).add(1); // First row

        for (int i = 1; i < numRows; i++) {
            List<Integer> prevRow = triangle.get(i - 1);
            List<Integer> newRow = new ArrayList<>();
            newRow.add(1); // First element of the row

            for (int j = 1; j < i; j++) {
                newRow.add(prevRow.get(j - 1) + prevRow.get(j)); // Middle elements
            }

            newRow.add(1); // Last element of the row
            triangle.add(newRow);
        }

        return triangle;
    }
}
```


### Kotlin

```kotlin
class Solution {
    fun generate(numRows: Int): List<List<Int>> {
        val triangle = mutableListOf<List<Int>>()

        if (numRows == 0) return triangle

        triangle.add(listOf(1)) // First row

        for (i in 1 until numRows) {
            val prevRow = triangle[i - 1]
            val newRow = mutableListOf<Int>()

            newRow.add(1) // First element of the row is always 1

            for (j in 1 until i) {
                newRow.add(prevRow[j - 1] + prevRow[j]) // Middle elements are sum of the two above
            }

            newRow.add(1) // Last element of the row is always 1
            triangle.add(newRow)
        }

        return triangle
    }
}
```


### Swift

```swift
class Solution {
    func generate(_ numRows: Int) -> [[Int]] {
        var triangle = [[Int]]()

        if numRows == 0 { return triangle }

        triangle.append([1]) // First row

        for i in 1..<numRows {
            let prevRow = triangle[i - 1]
            var newRow = [1] // First element of the row

            for j in 1..<i {
                newRow.append(prevRow[j - 1] + prevRow[j]) // Middle elements
            }

            newRow.append(1) // Last element of the row
            triangle.append(newRow)
        }

        return triangle
    }
}
```


### The End

