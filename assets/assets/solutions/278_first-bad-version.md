# First Bad Version

## Problem Statement

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version fails the quality check. Since each version is developed based on the previous one, all the versions after a bad version are also bad.

Suppose you have `n` versions `[1, 2, ..., n]` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given a function `bool isBadVersion(version)` that returns whether `version` is bad. Implement a method to find the first bad version. You should minimize the number of calls to the API.

## Input

```text
n = 5, bad = 4
```

## Output

```text
4
```

## Solutions

### Dart

```dart
class VersionControl {
  bool isBadVersion(int version) {
    // API implementation provided externally
    return false;
  }
}

class Solution extends VersionControl {
  int firstBadVersion(int n) {
    int start = 1, end = n, result = -1;

    while (start <= end) {
      int mid = start + (end - start) ~/ 2;
      if (isBadVersion(mid)) {
        result = mid;
        end = mid - 1;
      } else {
        start = mid + 1;
      }
    }

    return result;
  }
}
```

### C#

```csharp
/* The isBadVersion API is defined in the parent class VersionControl.
   bool IsBadVersion(int version); */

public class Solution : VersionControl {
    public int FirstBadVersion(int n) {
        int start = 1, end = n, result = -1;

        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (IsBadVersion(mid)) {
                result = mid;
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }

        return result;
    }
}
```

### Java

```java
/* The isBadVersion API is defined in the parent class VersionControl.
   boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int start = 1, end = n, result = -1;

        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (isBadVersion(mid)) {
                result = mid;
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }

        return result;
    }
}
```

### Kotlin

```kotlin
open class VersionControl {
    open fun isBadVersion(version: Int): Boolean {
        // API implementation provided externally
        return false
    }
}

class Solution : VersionControl() {
    override fun firstBadVersion(n: Int): Int {
        var start = 1
        var end = n
        var result = -1

        while (start <= end) {
            val mid = start + (end - start) / 2
            if (isBadVersion(mid)) {
                result = mid
                end = mid - 1
            } else {
                start = mid + 1
            }
        }

        return result
    }
}
```

### Swift

```swift
class VersionControl {
    func isBadVersion(_ version: Int) -> Bool {
        // API implementation provided externally
        return false
    }
}

class Solution : VersionControl {
    func firstBadVersion(_ n: Int) -> Int {
        var start = 1
        var end = n
        var result = -1

        while start <= end {
            let mid = start + (end - start) / 2
            if isBadVersion(mid) {
                result = mid
                end = mid - 1
            } else {
                start = mid + 1
            }
        }

        return result
    }
}
```

### The End

