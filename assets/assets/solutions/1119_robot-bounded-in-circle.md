# Robot Bounded in Circle

## Problem Statement

Given a string `instructions`, return `true` if the robot is bounded in a circle after following the instructions indefinitely, otherwise return `false`.

The robot can move in a plane:

- `'G'`: Move straight one unit in the direction it is currently facing.
- `'L'`: Turn left 90 degrees.
- `'R'`: Turn right 90 degrees.

The robot initially starts at the `(0, 0)` position and faces north.

## Input

```text
instructions = "GGLLGG"
```

## Output

```text
true
```

## Solutions

### Kotlin

```kotlin
class Solution {
    fun isRobotBounded(instructions: String): Boolean {
        var x = 0
        var y = 0
        var direction = 0 // 0 - North, 1 - East, 2 - South, 3 - West
        val dx = intArrayOf(0, 1, 0, -1)
        val dy = intArrayOf(1, 0, -1, 0)

        for (instruction in instructions) {
            when (instruction) {
                'G' -> {
                    x += dx[direction]
                    y += dy[direction]
                }
                'L' -> direction = (direction + 3) % 4
                'R' -> direction = (direction + 1) % 4
            }
        }

        return (x == 0 && y == 0) || direction != 0
    }
}
```

### Dart

```dart
bool isRobotBounded(String instructions) {
  int x = 0, y = 0, direction = 0;
  final dx = [0, 1, 0, -1];
  final dy = [1, 0, -1, 0];

  for (var instruction in instructions.split('')) {
    if (instruction == 'G') {
      x += dx[direction];
      y += dy[direction];
    } else if (instruction == 'L') {
      direction = (direction + 3) % 4;
    } else if (instruction == 'R') {
      direction = (direction + 1) % 4;
    }
  }

  return (x == 0 && y == 0) || direction != 0;
}
```

### C#

```csharp
public class Solution {
    public bool IsRobotBounded(string instructions) {
        int x = 0, y = 0, direction = 0;
        int[] dx = { 0, 1, 0, -1 };
        int[] dy = { 1, 0, -1, 0 };

        foreach (char instruction in instructions) {
            if (instruction == 'G') {
                x += dx[direction];
                y += dy[direction];
            } else if (instruction == 'L') {
                direction = (direction + 3) % 4;
            } else if (instruction == 'R') {
                direction = (direction + 1) % 4;
            }
        }

        return (x == 0 && y == 0) || direction != 0;
    }
}
```

### Java

```java
class Solution {
    public boolean isRobotBounded(String instructions) {
        int x = 0, y = 0, direction = 0;
        int[] dx = { 0, 1, 0, -1 };
        int[] dy = { 1, 0, -1, 0 };

        for (char instruction : instructions.toCharArray()) {
            if (instruction == 'G') {
                x += dx[direction];
                y += dy[direction];
            } else if (instruction == 'L') {
                direction = (direction + 3) % 4;
            } else if (instruction == 'R') {
                direction = (direction + 1) % 4;
            }
        }

        return (x == 0 && y == 0) || direction != 0;
    }
}
```

### Swift

```swift
class Solution {
    func isRobotBounded(_ instructions: String) -> Bool {
        var x = 0, y = 0, direction = 0
        let dx = [0, 1, 0, -1]
        let dy = [1, 0, -1, 0]

        for instruction in instructions {
            if instruction == "G" {
                x += dx[direction]
                y += dy[direction]
            } else if instruction == "L" {
                direction = (direction + 3) % 4
            } else if instruction == "R" {
                direction = (direction + 1) % 4
            }
        }

        return (x == 0 && y == 0) || direction != 0
    }
}
```

### The End