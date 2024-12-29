# Lemonade Change

## Problem Statement

At a lemonade stand, each lemonade costs `$5`. Customers are standing in a queue to buy from you, and they order one at a time. Each customer will pay with a `$5`, `$10`, or `$20` bill. You must provide the correct change to each customer. Initially, you have no bills in hand.

Return `true` if you can provide every customer with the correct change; otherwise, return `false`.

## Input

```text
bills = [5, 5, 5, 10, 20]
```

## Output

```text
true
```

## Solutions

### Dart

```dart
bool lemonadeChange(List<int> bills) {
  int fives = 0, tens = 0;

  for (int bill in bills) {
    if (bill == 5) {
      fives++;
    } else if (bill == 10) {
      if (fives == 0) return false;
      fives--;
      tens++;
    } else {
      if (tens > 0 && fives > 0) {
        tens--;
        fives--;
      } else if (fives >= 3) {
        fives -= 3;
      } else {
        return false;
      }
    }
  }

  return true;
}
```

### C#

```csharp
public class Solution {
    public bool LemonadeChange(int[] bills) {
        int fives = 0, tens = 0;

        foreach (int bill in bills) {
            if (bill == 5) {
                fives++;
            } else if (bill == 10) {
                if (fives == 0) return false;
                fives--;
                tens++;
            } else {
                if (tens > 0 && fives > 0) {
                    tens--;
                    fives--;
                } else if (fives >= 3) {
                    fives -= 3;
                } else {
                    return false;
                }
            }
        }

        return true;
    }
}
```

### Java

```java
class Solution {
    public boolean lemonadeChange(int[] bills) {
        int fives = 0, tens = 0;

        for (int bill : bills) {
            if (bill == 5) {
                fives++;
            } else if (bill == 10) {
                if (fives == 0) return false;
                fives--;
                tens++;
            } else {
                if (tens > 0 && fives > 0) {
                    tens--;
                    fives--;
                } else if (fives >= 3) {
                    fives -= 3;
                } else {
                    return false;
                }
            }
        }

        return true;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun lemonadeChange(bills: IntArray): Boolean {
        var fives = 0
        var tens = 0

        for (bill in bills) {
            when (bill) {
                5 -> fives++
                10 -> {
                    if (fives == 0) return false
                    fives--
                    tens++
                }
                20 -> {
                    if (tens > 0 && fives > 0) {
                        tens--
                        fives--
                    } else if (fives >= 3) {
                        fives -= 3
                    } else {
                        return false
                    }
                }
            }
        }

        return true
    }
}
```

### Swift

```swift
class Solution {
    func lemonadeChange(_ bills: [Int]) -> Bool {
        var fives = 0
        var tens = 0

        for bill in bills {
            if bill == 5 {
                fives += 1
            } else if bill == 10 {
                if fives == 0 {
                    return false
                }
                fives -= 1
                tens += 1
            } else {
                if tens > 0 && fives > 0 {
                    tens -= 1
                    fives -= 1
                } else if fives >= 3 {
                    fives -= 3
                } else {
                    return false
                }
            }
        }

        return true
    }
}
```


### The End