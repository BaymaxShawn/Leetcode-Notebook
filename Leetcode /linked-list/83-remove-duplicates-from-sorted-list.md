---
description: easy
---

# 😂 83 - Remove Duplicates from Sorted List

Given the `head` of a sorted linked list, _delete all duplicates such that each element appears only once_. Return _the linked list **sorted** as well_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/01/04/list1.jpg)

<pre><code><strong>Input: head = [1,1,2]
</strong><strong>Output: [1,2]
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/01/04/list2.jpg)

<pre><code><strong>Input: head = [1,1,2,3,3]
</strong><strong>Output: [1,2,3]
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the list is in the range `[0, 300]`.
* `-100 <= Node.val <= 100`
* The list is guaranteed to be **sorted** in ascending order.

## Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:

        cur = head

        while cur and cur.next:
            if cur.next.val == cur.val:
                cur.next = cur.next.next
            else:
                cur = cur.next
        
        return head
```
