# 😃 1512 - Number of Good Pairs

````python

class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        res = 0 

        dis = collections.Counter(nums)

        print(dis)
        for i, value in dis.items():

            if value >=2:
                res += value*(value-1)//2
            
        return res
```
````

```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        counts = defaultdict(int)
        ans = 0
        
        for num in nums:
            ans += counts[num]
            counts[num] += 1
        print(counts)
        return ans
```
