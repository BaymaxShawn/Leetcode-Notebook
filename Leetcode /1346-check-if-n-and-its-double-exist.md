# 🤷 1346 - Check If N and Its Double Exist

Given an array `arr` of integers, check if there exist two indices `i` and `j` such that :

* `i != j`
* `0 <= i, j < arr.length`
* `arr[i] == 2 * arr[j]`

&#x20;

**Example 1:**

<pre><code><strong>Input: arr = [10,2,5,3]
</strong><strong>Output: true
</strong><strong>Explanation: For i = 0 and j = 2, arr[i] == 10 == 2 * 5 == 2 * arr[j]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: arr = [3,1,7,11]
</strong><strong>Output: false
</strong><strong>Explanation: There is no i and j that satisfy the conditions.
</strong></code></pre>

## Solution

#### Python

```python
class Solution:
    def checkIfExist(self, arr: List[int]) -> bool:

        num = set()
        for i in arr:
            if 2*i in num or (i//2 in num and i%2 == 0):
                return True
            num.add(i)
        return False
```
