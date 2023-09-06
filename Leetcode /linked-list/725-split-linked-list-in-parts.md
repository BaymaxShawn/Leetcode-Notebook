---
description: sep 6 ,2023 daily
---

# 😂 725 - Split Linked List in Parts

## Solution:

{% embed url="https://www.youtube.com/watch?v=-OTlqdrxrVI" %}

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def splitListToParts(self, head: Optional[ListNode], k: int) -> List[Optional[ListNode]]:
        length, cur = 0,head
        while cur:
            cur = cur.next
            length += 1

        base_len, remainder = length // k , length % k
        cur = head 
        res = []
        for i in range(k):
            res.append(cur)
            for j in range(base_len - 1 + (1 if remainder else 0)):
                if not cur:
                    break
                cur = cur.next
            remainder -= (1 if remainder else 0)
            if cur:
                cur.next , cur = None,cur.next
        
        return res 
```
