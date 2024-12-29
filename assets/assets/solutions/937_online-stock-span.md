# Online Stock Span

## Problem Statement

The StockSpanner class collects daily price quotes for some stock and returns the span of that stock's price for the current day.

The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backward) for which the price of the stock was less than or equal to today's price.

Implement the `StockSpanner` class:

- `StockSpanner()` Initializes the object of the class.
- `int next(int price)` Returns the span of the stock's price for the current day.

## Input

```text
["StockSpanner", "next", "next", "next", "next", "next", "next", "next"]
[[], [100], [80], [60], [70], [60], [75], [85]]
```

## Output

```text
[null, 1, 1, 1, 2, 1, 4, 6]
```

## Solutions

### Kotlin

```kotlin
class StockSpanner {
    private val prices = mutableListOf<Int>()
    private val spans = mutableListOf<Int>()

    fun next(price: Int): Int {
        var span = 1
        while (prices.isNotEmpty() && prices.last() <= price) {
            prices.removeAt(prices.size - 1)
            span += spans.removeAt(spans.size - 1)
        }
        prices.add(price)
        spans.add(span)
        return span
    }
}
```

### Dart

```dart
class StockSpanner {
  final List<int> prices = [];
  final List<int> spans = [];

  int next(int price) {
    int span = 1;
    while (prices.isNotEmpty && prices.last <= price) {
      prices.removeLast();
      span += spans.removeLast();
    }
    prices.add(price);
    spans.add(span);
    return span;
  }
}
```

### C#

```csharp
public class StockSpanner {
    private Stack<int> prices;
    private Stack<int> spans;

    public StockSpanner() {
        prices = new Stack<int>();
        spans = new Stack<int>();
    }

    public int Next(int price) {
        int span = 1;
        while (prices.Count > 0 && prices.Peek() <= price) {
            prices.Pop();
            span += spans.Pop();
        }
        prices.Push(price);
        spans.Push(span);
        return span;
    }
}
```

### Java

```java
import java.util.Stack;

class StockSpanner {
    private Stack<Integer> prices;
    private Stack<Integer> spans;

    public StockSpanner() {
        prices = new Stack<>();
        spans = new Stack<>();
    }

    public int next(int price) {
        int span = 1;
        while (!prices.isEmpty() && prices.peek() <= price) {
            prices.pop();
            span += spans.pop();
        }
        prices.push(price);
        spans.push(span);
        return span;
    }
}
```

### Swift

```swift
class StockSpanner {
    private var prices: [Int] = []
    private var spans: [Int] = []

    func next(_ price: Int) -> Int {
        var span = 1
        while !prices.isEmpty && prices.last! <= price {
            prices.removeLast()
            span += spans.removeLast()
        }
        prices.append(price)
        spans.append(span)
        return span
    }
}
```

### The End