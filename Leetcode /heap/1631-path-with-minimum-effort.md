# 🧐 1631 -  Path With Minimum Effort

## Tip #1

`heapq.heappop()` 是 Python 中 `heapq` 模块提供的一个函数，用于从堆（heap）数据结构中弹出并返回堆顶部的最小元素。堆是一种特殊的树状数据结构，其中每个节点的值都小于或等于其子节点的值。这使得堆的根节点始终是堆中的最小值（最小堆）或最大值（最大堆），具体取决于您的实现。

以下是 `heapq.heappop()` 的基本用法示例：

```python
pythonCopy codeimport heapq

# 创建一个最小堆
heap = [3, 1, 5, 7, 2, 4]

# 使用heapq.heapify()将列表转换为堆
heapq.heapify(heap)

# 弹出并返回堆中的最小元素
min_element = heapq.heappop(heap)

print(min_element)  # 输出：1
print(heap)         # 输出：[2, 3, 4, 7, 5]
```

在示例中，我们首先创建了一个包含整数的列表，然后使用 `heapq.heapify()` 将其转换为最小堆。接下来，我们使用 `heapq.heappop()` 弹出并返回了堆中的最小元素，即 1。

`heapq` 模块提供了一些其他与堆相关的函数，如插入元素、获取最小元素等，以便于处理堆数据结构。这在很多算法和数据结构问题中都非常有用，因为堆可以用来高效地维护一组数据中的最小（或最大）元素。

{% embed url="https://www.youtube.com/watch?v=XQlxCCx2vI4" %}

```python
class Solution:
    def minimumEffortPath(self, heights: List[List[int]]) -> int:
        Row, Col = len(heights),len(heights[0])

        minHeap = [[0,0,0]]
        visit = set()
        direction = [[1,0],[0,1],[-1,0],[0,-1]]

        while minHeap:
            diff,r,c = heapq.heappop(minHeap)

            if (r,c) in visit:
                continue
            visit.add((r,c))
            if (r,c) == (Row-1,Col-1):
                return diff
            
            for dr,dc in direction:
                newR,newC = r + dr, c + dc
                if (newR<0 or newC <0 or newR== Row or newC == Col or (newR,newC)in visit):
                    continue
                newDiff = max(diff,abs(heights[r][c] - heights[newR][newC] ))          
                heapq.heappush(minHeap,[newDiff,newR,newC])
```
