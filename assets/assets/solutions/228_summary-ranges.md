# Summary Ranges

## Problem Statement

Given a sorted integer array `nums` without duplicates, return the summary of its ranges. A range `[a->b]` represents a sequence of consecutive integers from `a` to `b`.

## Input

```text
nums = [0, 1, 2, 4, 5, 7]
```

## Output

```text
["0->2", "4->5", "7"]
```

## Solutions

### Dart

```dart
List<String> summaryRanges(List<int> nums) {
  List<String> result = [];
  int i = 0;

  while (i < nums.length) {
    int start = nums[i];
    int end = start;

    while (i + 1 < nums.length && nums[i + 1] == nums[i] + 1) {
      i++;
      end = nums[i];
    }

    if (start == end) {
      result.add("$start");
    } else {
      result.add("$start->$end");
    }

    i++;
  }

  return result;
}
```

### C#

```csharp
public class Solution {
    public IList<string> SummaryRanges(int[] nums) {
        List<string> result = new List<string>();
        int i = 0;

        while (i < nums.Length) {
            int start = nums[i];
            int end = start;

            while (i + 1 < nums.Length && nums[i + 1] == nums[i] + 1) {
                i++;
                end = nums[i];
            }

            if (start == end) {
                result.Add(start.ToString());
            } else {
                result.Add($"{start}->{end}");
            }

            i++;
        }

        return result;
    }
}
```

### Java

```java
class Solution {
    public List<String> summaryRanges(int[] nums) {
        List<String> result = new ArrayList<>();
        int i = 0;

        while (i < nums.length) {
            int start = nums[i];
            int end = start;

            while (i + 1 < nums.length && nums[i + 1] == nums[i] + 1) {
                i++;
                end = nums[i];
            }

            if (start == end) {
                result.add(String.valueOf(start));
            } else {
                result.add(start + "->" + end);
            }

            i++;
        }

        return result;
    }
}
```

### Kotlin

```kotlin
class Solution {
    fun summaryRanges(nums: IntArray): List<String> {
        val result = mutableListOf<String>()
        var i = 0
        
        while (i < nums.size) {
            val start = nums[i]
            var end = start
            
            while (i + 1 < nums.size && nums[i + 1] == nums[i] + 1) {
                i++
                end = nums[i]
            }
            
            if (start == end) {
                result.add(start.toString())
            } else {
                result.add("$start->$end")
            }
            
            i++
        }
        
        return result
    }
}
```

### Swift

```swift
class Solution {
    func summaryRanges(_ nums: [Int]) -> [String] {
        var result = [String]()
        var i = 0
        
        while i < nums.count {
            let start = nums[i]
            var end = start
            
            while i + 1 < nums.count && nums[i + 1] == nums[i] + 1 {
                i += 1
                end = nums[i]
            }
            
            if start == end {
                result.append("\(start)")
            } else {
                result.append("\(start)->\(end)")
            }
            
            i += 1
        }
        
        return result
    }
}
```


### The End

