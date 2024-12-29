# Happy Number

## Problem Statement

Write an algorithm to determine if a number `n` is happy.

A happy number is defined by the following process:

1. Starting with any positive integer, replace the number by the sum of the squares of its digits.
2. Repeat the process until the number equals 1 (it will stay at 1), or it loops endlessly in a cycle which does not include 1.
3. Return `true` if the number is a happy number, otherwise return `false`.

## Input

```text
n = 19
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool isHappy(int n) {
  int getNext(int num) {
    int sum = 0;
    while (num > 0) {
      int digit = num % 10;
      sum += digit * digit;
      num ~/= 10;
    }
    return sum;
  }

  int slow = n;
  int fast = getNext(n);

  while (fast != 1 && slow != fast) {
    slow = getNext(slow);
    fast = getNext(getNext(fast));
  }

  return fast == 1;
}
```

### C#

```csharp
public class Solution {
    public bool IsHappy(int n) {
        int GetNext(int num) {
            int sum = 0;
            while (num > 0) {
                int digit = num % 10;
                sum += digit * digit;
                num /= 10;
            }
            return sum;
        }

        int slow = n;
        int fast = GetNext(n);

        while (fast != 1 && slow != fast) {
            slow = GetNext(slow);
            fast = GetNext(GetNext(fast));
        }

        return fast == 1;
    }
}
```

### Java

```java
class Solution {
    public boolean isHappy(int n) {
        int getNext(int num) {
            int sum = 0;
            while (num > 0) {
                int digit = num % 10;
                sum += digit * digit;
                num /= 10;
            }
            return sum;
        }

        int slow = n;
        int fast = getNext(n);

        while (fast != 1 && slow != fast) {
            slow = getNext(slow);
            fast = getNext(getNext(fast));
        }

        return fast == 1;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isHappy(n: Int): Boolean {
        var slow = n
        var fast = getNext(n)
        while (fast != 1 && slow != fast) {
            slow = getNext(slow)
            fast = getNext(getNext(fast))
        }
        return fast == 1
    }

    private fun getNext(n: Int): Int {
        var sum = 0
        var num = n
        while (num > 0) {
            val digit = num % 10
            sum += digit * digit
            num /= 10
        }
        return sum
    }
}
```

### Swift

```swift
class Solution {
    func isHappy(_ n: Int) -> Bool {
        func getNext(_ num: Int) -> Int {
            var sum = 0
            var num = num
            while num > 0 {
                let digit = num % 10
                sum += digit * digit
                num /= 10
            }
            return sum
        }

        var slow = n
        var fast = getNext(n)

        while fast != 1 && slow != fast {
            slow = getNext(slow)
            fast = getNext(getNext(fast))
        }

        return fast == 1
    }
}
```

### The End

