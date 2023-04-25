---
description: medium daily question 2023/04/25
---

# 😅 2336 - Smallest Number in Infinite Set

You have a set which contains all positive integers `[1, 2, 3, 4, 5, ...]`.

Implement the `SmallestInfiniteSet` class:

* `SmallestInfiniteSet()` Initializes the **SmallestInfiniteSet** object to contain **all** positive integers.
* `int popSmallest()` **Removes** and returns the smallest integer contained in the infinite set.
* `void addBack(int num)` **Adds** a positive integer `num` back into the infinite set, if it is **not** already in the infinite set.

&#x20;

**Example 1:**

<pre><code><strong>Input
</strong>["SmallestInfiniteSet", "addBack", "popSmallest", "popSmallest", "popSmallest", "addBack", "popSmallest", "popSmallest", "popSmallest"]
[[], [2], [], [], [], [1], [], [], []]
<strong>Output
</strong>[null, null, 1, 2, 3, null, 1, 4, 5]

<strong>Explanation
</strong>SmallestInfiniteSet smallestInfiniteSet = new SmallestInfiniteSet();
smallestInfiniteSet.addBack(2);    // 2 is already in the set, so no change is made.
smallestInfiniteSet.popSmallest(); // return 1, since 1 is the smallest number, and remove it from the set.
smallestInfiniteSet.popSmallest(); // return 2, and remove it from the set.
smallestInfiniteSet.popSmallest(); // return 3, and remove it from the set.
smallestInfiniteSet.addBack(1);    // 1 is added back to the set.
smallestInfiniteSet.popSmallest(); // return 1, since 1 was added back to the set and
                                   // is the smallest number, and remove it from the set.
smallestInfiniteSet.popSmallest(); // return 4, and remove it from the set.
smallestInfiniteSet.popSmallest(); // return 5, and remove it from the set.
</code></pre>

&#x20;

**Constraints:**

* `1 <= num <= 1000`
* At most `1000` calls will be made **in total** to `popSmallest` and `addBack`.

## Solution

[https://www.youtube.com/watch?v=D2HXOwAnNXA](https://www.youtube.com/watch?v=D2HXOwAnNXA)

```python
class SmallestInfiniteSet:

    def __init__(self):
        self.seen = [False] * 1001
        

    def popSmallest(self) -> int:
        for i in range(1,1001):
            if not self.seen[i] :
                self.seen[i] = True
                return i

    def addBack(self, num: int) -> None:
        self.seen[num] = False

```
