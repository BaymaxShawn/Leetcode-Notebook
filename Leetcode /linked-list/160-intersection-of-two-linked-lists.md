# ☺ 160 - Intersection of Two Linked Lists

{% embed url="https://www.youtube.com/watch?v=D0X0BONOQhI" %}

```python3
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        a , b = headA,headB

        while a != b:
            a = headB if not a else a.next
            b = headA if not b else b.next
        
        return a
```
