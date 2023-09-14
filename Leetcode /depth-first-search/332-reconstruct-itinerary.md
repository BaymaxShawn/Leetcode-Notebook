# 😞 332 - Reconstruct Itinerary

{% embed url="https://cloud.tencent.com/developer/article/1930785" %}

{% embed url="https://www.youtube.com/watch?v=ZyB_gQ8vqGA" %}

```python
class Solution:
    def findItinerary(self, tickets: List[List[str]]) -> List[str]:
        adj = {src:[] for src,dst in tickets}
        tickets.sort()

        for src , dst in tickets:
            adj[src].append(dst)

        res = ['JFK']
        def dfs(src):
            if len(res) == len(tickets) +1:
                return True
            if src not in adj:
                return False
            
            temp = list(adj[src])
            for i,v in enumerate(adj[src]):
                adj[src].pop(i)
                res.append(v)
                if dfs(v): return True
                adj[src].insert(i,v)
                res.pop()

            return False

        dfs('JFK')
        return res

```
