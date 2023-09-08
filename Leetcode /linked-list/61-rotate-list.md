# 😜 61 - Rotate List

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:

        if not head:
            return None
        if not head.next:
            return head

        tem = head
        l = 1
        while tem.next:
            tem = tem.next
            l +=1 
        tem.next = head

        cur = head
        for i in range(l - k%l -1):
            cur = cur.next
        new_head = cur.next

        cur.next = None
    
        return new_head



```
