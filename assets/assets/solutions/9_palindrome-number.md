# Palindrome Number

## Problem Statement

Given an integer `x`, return `true` if `x` is a palindrome, and `false` otherwise.

An integer is a palindrome when it reads the same backward as forward. For example, `121` is a palindrome while `123` is not.

## Input

```text
x = 121
```

## Output

```text
true  
(Explanation: `121` reads as `121` from both directions.)
```

## Solutions

### Dart

```dart
bool isPalindrome(int x) {
  if (x < 0 || (x % 10 == 0 && x != 0)) return false;

  int reversed = 0;
  int num = x;
  while (num > reversed) {
    reversed = reversed * 10 + num % 10;
    num ~/= 10;
  }

  return num == reversed || num == reversed ~/ 10;
}

void main() {
  print(isPalindrome(121)); // Output: true
  print(isPalindrome(-121)); // Output: false
  print(isPalindrome(10)); // Output: false
}
```

### C#

```csharp
public class Solution {
    public bool IsPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) return false;

        int reversed = 0;
        int num = x;
        while (num > reversed) {
            reversed = reversed * 10 + num % 10;
            num /= 10;
        }

        return num == reversed || num == reversed / 10;
    }
}
```

### Java

```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) return false;

        int reversed = 0;
        int num = x;
        while (num > reversed) {
            reversed = reversed * 10 + num % 10;
            num /= 10;
        }

        return num == reversed || num == reversed / 10;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun isPalindrome(x: Int): Boolean {
        if (x < 0 || (x % 10 == 0 && x != 0)) return false
        var reversed = 0
        var num = x
        while (num > reversed) {
            reversed = reversed * 10 + num % 10
            num /= 10
        }
        return num == reversed || num == reversed / 10
    }
}
```

### Swift

```swift
class Solution {
    func isPalindrome(_ x: Int) -> Bool {
        if x < 0 || (x % 10 == 0 && x != 0) { return false }

        var reversed = 0
        var num = x
        while num > reversed {
            reversed = reversed * 10 + num % 10
            num /= 10
        }

        return num == reversed || num == reversed / 10
    }
}

let solution = Solution()
print(solution.isPalindrome(121)) // Output: true
print(solution.isPalindrome(-121)) // Output: false
print(solution.isPalindrome(10)) // Output: false
```


### The End

