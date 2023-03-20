# ☺ 167 - Two Sum II - Input Array Is Sorted

Given a **1-indexed** array of integers `numbers` that is already _**sorted in non-decreasing order**_, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

&#x20;

**Example 1:**

<pre><code><strong>Input: numbers = [2,7,11,15], target = 9
</strong><strong>Output: [1,2]
</strong><strong>Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: numbers = [2,3,4], target = 6
</strong><strong>Output: [1,3]
</strong><strong>Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: numbers = [-1,0], target = -1
</strong><strong>Output: [1,2]
</strong><strong>Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
</strong></code></pre>

## Solution

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
              
        #O（log n)
        #binary search

        l,r = 0, len(numbers) -1

        while l<r:
            if numbers[l] + numbers[r] == target:
                return [l+1,r+1]
            elif numbers[l] + numbers[r] > target:
                r -= 1
            else:
                l+=1 


        # O (n^2)
        # brute force
        
        for i in range(len(numbers)):
            for j in range(len(numbers)):
                if numbers[i] + numbers[j] == target and i != j:
                    return [i+1,j+1]
        

        
```
