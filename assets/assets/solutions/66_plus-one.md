# Plus One

## Problem Statement

Given a non-empty array of decimal digits representing a non-negative integer, increment one to the integer. The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

## Input

```text
digits = [1,2,3]
```

## Output

```text
[1,2,4]  
(Explanation: The array represents the integer 123. Incrementing by one gives 124.)
```

## Solutions

### Dart

```dart
List<int> plusOne(List<int> digits) {
  for (int i = digits.length - 1; i >= 0; i--) {
    if (digits[i] < 9) {
      digits[i]++;
      return digits;
    }
    digits[i] = 0;
  }

  // If all digits are 9
  digits.insert(0, 1);
  return digits;
}

void main() {
  print(plusOne([1, 2, 3])); // Output: [1, 2, 4]
  print(plusOne([4, 3, 2, 1])); // Output: [4, 3, 2, 2]
  print(plusOne([9, 9, 9])); // Output: [1, 0, 0, 0]
}
```

### C#

```csharp
public class Solution {
    public int[] PlusOne(int[] digits) {
        for (int i = digits.Length - 1; i >= 0; i--) {
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }

        // If all digits are 9
        int[] result = new int[digits.Length + 1];
        result[0] = 1;
        return result;
    }
}
```

### Java

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for (int i = digits.length - 1; i >= 0; i--) {
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }

        // If all digits are 9
        int[] result = new int[digits.length + 1];
        result[0] = 1;
        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun plusOne(digits: IntArray): IntArray {
        for (i in digits.indices.reversed()) {
            if (digits[i] < 9) {
                digits[i]++
                return digits
            }
            digits[i] = 0
        }

        val result = IntArray(digits.size + 1)
        result[0] = 1
        return result
    }
}
```

### Swift

```swift
class Solution {
    func plusOne(_ digits: [Int]) -> [Int] {
        var digits = digits
        for i in stride(from: digits.count - 1, through: 0, by: -1) {
            if digits[i] < 9 {
                digits[i] += 1
                return digits
            }
            digits[i] = 0
        }

        // If all digits are 9
        digits.insert(1, at: 0)
        return digits
    }
}

let solution = Solution()
print(solution.plusOne([1, 2, 3])) // Output: [1, 2, 4]
print(solution.plusOne([4, 3, 2, 1])) // Output: [4, 3, 2, 2]
print(solution.plusOne([9, 9, 9])) // Output: [1, 0, 0, 0]
```

### The End

