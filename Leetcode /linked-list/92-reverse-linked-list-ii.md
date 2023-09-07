---
description: sep 6 2023 daily
---

# 🧠 92 - Reverse Linked List II

{% embed url="https://www.youtube.com/watch?v=RF_M9tX4Eag" %}

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        dummy = ListNode(0,head)

        # 1
        leftPrev , cur = dummy ,head
        for i in range(left - 1):
            leftPrev, cur = cur , cur.next

        # 2
        prev = None
        for i in range ( right - left +1 ):
            temNext = cur.next
            cur.next = prev
            prev, cur = cur, temNext
        
        # 3 
        leftPrev.next.next = cur
        leftPrev.next = prev

        return dummy.next
```
