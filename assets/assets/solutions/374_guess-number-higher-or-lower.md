# Guess Number Higher or Lower

## Problem Statement

We are playing the Guess Game. The game is as follows:

1. I pick a number from `1` to `n`. You have to guess which number I picked.
2. Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess.
3. You call a pre-defined API `guess(int num)` which returns:
   - `-1`: My number is lower.
   - `1`: My number is higher.
   - `0`: Your guess is correct.

Implement a function to find the number I picked.

---

## Input

```text
n = 10
pick = 6
```

## Output

```text
6
```


## Solutions

### Dart

```dart
class GuessGame {
  int guess(int num) {
    // This is a placeholder for the actual guess API.
    return 0;
  }
}

class Solution extends GuessGame {
  int guessNumber(int n) {
    int left = 1, right = n;
    while (left < right) {
      int mid = left + (right - left) ~/ 2;
      int res = guess(mid);
      if (res == 0) return mid;
      if (res < 0) {
        right = mid;
      } else {
        left = mid + 1;
      }
    }
    return left;
  }
}
```

### C#

```csharp
public class GuessGame {
    public int Guess(int num) {
        // This is a placeholder for the actual guess API.
        return 0;
    }
}

public class Solution : GuessGame {
    public int GuessNumber(int n) {
        int left = 1, right = n;
        while (left < right) {
            int mid = left + (right - left) / 2;
            int res = Guess(mid);
            if (res == 0) return mid;
            if (res < 0) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

---

### Java

```java
public class GuessGame {
    int guess(int num) {
        // This is a placeholder for the actual guess API.
        return 0;
    }
}

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int left = 1, right = n;
        while (left < right) {
            int mid = left + (right - left) / 2;
            int res = guess(mid);
            if (res == 0) return mid;
            if (res < 0) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```


### Kotlin

```kotlin
open class GuessGame {
    fun guess(num: Int): Int {
        // Placeholder for the actual guess API.
        return 0
    }
}

class Solution : GuessGame() {
    override fun guessNumber(n: Int): Int {
        var left = 1
        var right = n
        while (left < right) {
            val mid = left + (right - left) / 2
            val res = guess(mid)
            when {
                res == 0 -> return mid
                res < 0 -> right = mid
                else -> left = mid + 1
            }
        }
        return left
    }
}
```

### Swift

```swift
class GuessGame {
    func guess(_ num: Int) -> Int {
        // This is a placeholder for the actual guess API.
        return 0
    }
}

class Solution : GuessGame {
    func guessNumber(_ n: Int) -> Int {
        var left = 1
        var right = n
        while left < right {
            let mid = left + (right - left) / 2
            let res = guess(mid)
            if res == 0 {
                return mid
            } else if res < 0 {
                right = mid
            } else {
                left = mid + 1
            }
        }
        return left
    }
}
```

### The End

