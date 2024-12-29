# Robot Return to Origin

## Problem Statement

There is a robot starting at the origin point `(0, 0)` on a 2D plane. Given a string `moves` that represents the sequence of its moves, check if the robot returns to the origin after it finishes all its moves.

The moves string consists of characters `'U'` (up), `'D'` (down), `'L'` (left), and `'R'` (right). Each move shifts the robot by one unit in the corresponding direction.

## Input

```text
moves = "UD"
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun judgeCircle(moves: String): Boolean {
        var x = 0
        var y = 0

        for (move in moves) {
            when (move) {
                'U' -> y++
                'D' -> y--
                'L' -> x--
                'R' -> x++
            }
        }

        return x == 0 && y == 0
    }
}

fun main() {
    val moves = "UD"
    val solution = Solution()
    println("Does the robot return to the origin? ${solution.judgeCircle(moves)}") // Output: true
}
```


### Dart

```dart
bool judgeCircle(String moves) {
  int x = 0;
  int y = 0;

  for (var move in moves.split('')) {
    if (move == 'U') y++;
    else if (move == 'D') y--;
    else if (move == 'L') x--;
    else if (move == 'R') x++;
  }

  return x == 0 && y == 0;
}

void main() {
  String moves = "UD";
  print("Does the robot return to the origin? ${judgeCircle(moves)}"); // Output: true
}
```


### C#

```csharp
public class Solution {
    public bool JudgeCircle(string moves) {
        int x = 0, y = 0;

        foreach (char move in moves) {
            if (move == 'U') y++;
            else if (move == 'D') y--;
            else if (move == 'L') x--;
            else if (move == 'R') x++;
        }

        return x == 0 && y == 0;
    }
}
```


### Java

```java
class Solution {
    public boolean judgeCircle(String moves) {
        int x = 0, y = 0;

        for (char move : moves.toCharArray()) {
            if (move == 'U') y++;
            else if (move == 'D') y--;
            else if (move == 'L') x--;
            else if (move == 'R') x++;
        }

        return x == 0 && y == 0;
    }
}
```


### Swift

```swift
class Solution {
    func judgeCircle(_ moves: String) -> Bool {
        var x = 0
        var y = 0

        for move in moves {
            switch move {
            case "U": y += 1
            case "D": y -= 1
            case "L": x -= 1
            case "R": x += 1
            default: break
            }
        }

        return x == 0 && y == 0
    }
}

// Example usage
let moves = "UD"
let solution = Solution()
print("Does the robot return to the origin? \(solution.judgeCircle(moves))") // Output: true
```

### The End