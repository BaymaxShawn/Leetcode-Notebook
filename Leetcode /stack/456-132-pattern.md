# 😁 456 - 132 Pattern

[https://www.youtube.com/watch?v=q5ANAl8Z458](https://www.youtube.com/watch?v=q5ANAl8Z458)

```python3
class Solution:
    def find132pattern(self, nums: List[int]) -> bool:
        stack = []
        minNum = nums[0]

        for n in nums[1:]:
            while stack and n >= stack[-1][0]:
                stack.pop()
            if stack and n > stack[-1][1]:
                return True

            stack.append([n,minNum])
            minNum = min(n,minNum)

        return False
```
