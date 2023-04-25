---
description: easy
---

# 😌 203 - Remove Linked List Elements

Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return _the new head_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/03/06/removelinked-list.jpg)

<pre><code><strong>Input: head = [1,2,6,3,4,5,6], val = 6
</strong><strong>Output: [1,2,3,4,5]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: head = [], val = 1
</strong><strong>Output: []
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: head = [7,7,7,7], val = 7
</strong><strong>Output: []
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the list is in the range `[0, 104]`.
* `1 <= Node.val <= 50`
* `0 <= val <= 50`

## Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:

        dummy = ListNode(0)
        dummy.next = head
        
        l,r = dummy,head
        while r:
            if r.val == val:
                l.next = r.next
            else:
                l = r
            r = r.next
            
        return dummy.next
```
