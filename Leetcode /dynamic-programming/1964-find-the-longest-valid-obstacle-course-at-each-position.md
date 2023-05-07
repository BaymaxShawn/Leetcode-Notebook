---
description: hard 05/07/2023
---

# 😞 1964 - Find the Longest Valid Obstacle Course at Each Position

You want to build some obstacle courses. You are given a **0-indexed** integer array `obstacles` of length `n`, where `obstacles[i]` describes the height of the `ith` obstacle.

For every index `i` between `0` and `n - 1` (**inclusive**), find the length of the **longest obstacle course** in `obstacles` such that:

* You choose any number of obstacles between `0` and `i` **inclusive**.
* You must include the `ith` obstacle in the course.
* You must put the chosen obstacles in the **same order** as they appear in `obstacles`.
* Every obstacle (except the first) is **taller** than or the **same height** as the obstacle immediately before it.

Return _an array_ `ans` _of length_ `n`, _where_ `ans[i]` _is the length of the **longest obstacle course** for index_ `i` _as described above_.

&#x20;

**Example 1:**

<pre><code><strong>Input: obstacles = [1,2,3,2]
</strong><strong>Output: [1,2,3,3]
</strong><strong>Explanation: The longest valid obstacle course at each position is:
</strong>- i = 0: [1], [1] has length 1.
- i = 1: [1,2], [1,2] has length 2.
- i = 2: [1,2,3], [1,2,3] has length 3.
- i = 3: [1,2,3,2], [1,2,2] has length 3.
</code></pre>

**Example 2:**

<pre><code><strong>Input: obstacles = [2,2,1]
</strong><strong>Output: [1,2,1]
</strong><strong>Explanation: The longest valid obstacle course at each position is:
</strong>- i = 0: [2], [2] has length 1.
- i = 1: [2,2], [2,2] has length 2.
- i = 2: [2,2,1], [1] has length 1.
</code></pre>

**Example 3:**

<pre><code><strong>Input: obstacles = [3,1,5,6,4,2]
</strong><strong>Output: [1,1,2,3,2,2]
</strong><strong>Explanation: The longest valid obstacle course at each position is:
</strong>- i = 0: [3], [3] has length 1.
- i = 1: [3,1], [1] has length 1.
- i = 2: [3,1,5], [3,5] has length 2. [1,5] is also valid.
- i = 3: [3,1,5,6], [3,5,6] has length 3. [1,5,6] is also valid.
- i = 4: [3,1,5,6,4], [3,4] has length 2. [1,4] is also valid.
- i = 5: [3,1,5,6,4,2], [1,2] has length 2.
</code></pre>

&#x20;

**Constraints:**

* `n == obstacles.length`
* `1 <= n <= 105`
* `1 <= obstacles[i] <= 107`

## Solution

[https://www.youtube.com/watch?v=Xq9VT7p0lic](https://www.youtube.com/watch?v=Xq9VT7p0lic)

```python
class Solution:
    def longestObstacleCourseAtEachPosition(self, obstacles: List[int]) -> List[int]:

        res = []
        dp = [10**8]* (len(obstacles)+1)

        for n in obstacles:
            i = bisect.bisect(dp,n)
            res.append(i+1)
            dp[i] = n
        
        return res

```
