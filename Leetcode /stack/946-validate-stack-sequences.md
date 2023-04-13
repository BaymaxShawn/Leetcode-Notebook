---
description: medium 2023/04/13
---

# 🙁 946 - Validate Stack Sequences

Given two integer arrays `pushed` and `popped` each with distinct values, return `true` _if this could have been the result of a sequence of push and pop operations on an initially empty stack, or_ `false` _otherwise._

&#x20;

**Example 1:**

<pre><code><strong>Input: pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
</strong><strong>Output: true
</strong><strong>Explanation: We might do the following sequence:
</strong>push(1), push(2), push(3), push(4),
pop() -> 4,
push(5),
pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1
</code></pre>

**Example 2:**

<pre><code><strong>Input: pushed = [1,2,3,4,5], popped = [4,3,5,1,2]
</strong><strong>Output: false
</strong><strong>Explanation: 1 cannot be popped before 2.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= pushed.length <= 1000`
* `0 <= pushed[i] <= 1000`
* All the elements of `pushed` are **unique**.
* `popped.length == pushed.length`
* `popped` is a permutation of `pushed`.

## Solution

```python
class Solution:
    def validateStackSequences(self, pushed: List[int], popped: List[int]) -> bool:

        count = 0 
        stack = []
        
        for i in pushed:
            stack.append(i)
            while stack and count < len(popped) and stack[-1] == popped[count]:
                stack.pop()
                count += 1
        
        return count == len(popped)
```
