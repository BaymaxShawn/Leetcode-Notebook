# 😆 2038 - Remove Colored Pieces if Both Neighbors are the Same Color

```python
class Solution:
    def winnerOfGame(self, colors: str) -> bool:
        res= {"A":0,"B":0}
        l,r,f = 0,0,0
        for i in range(len(colors)):
            if colors[i] == "A":
                r = f 
                r += 1
                if r -l >= 3:
                    res["A"] += 1
                f = r
            else :
                f += 1
                l = f
                if f - r >= 3:
                    res["B"] += 1

        if res["A"] > res["B"]:
            return True
        else:
            return False
                
                
                

                

```

```python
class Solution:
    def winnerOfGame(self, colors: str) -> bool:

        a = b = 0

        for i in range(1,len(colors)-1):
            if colors[i-1] == colors[i] == colors[i+1]:
                if colors[i] == "A":
                    a += 1
                else:
                    b += 1
                
        return a > b
                
                
                

                

```
