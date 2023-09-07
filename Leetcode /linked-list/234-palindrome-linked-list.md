# 😌 234 - Palindrome Linked List

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        res = []
        
        while head:
            res.append(head.val)
            head = head.next
        
        return res == res[::-1]

```
