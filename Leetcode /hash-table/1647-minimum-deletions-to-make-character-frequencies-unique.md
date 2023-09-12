# 😌 1647 - Minimum Deletions to Make Character Frequencies Unique

[https://www.youtube.com/watch?v=h8AZEN49gTc](https://www.youtube.com/watch?v=h8AZEN49gTc)

```python
class Solution:
    def minDeletions(self, s: str) -> int:
        
        count = collections.Counter(s)
        print(count)
        freqset = set()
        res = 0

        for i , fre in count.items():
            while fre > 0 and fre in freqset:
                fre -= 1
                res += 1
            freqset.add(fre)
        
        return res

```
