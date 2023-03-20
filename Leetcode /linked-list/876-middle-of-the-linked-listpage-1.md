# 🥲 876 - Middle of the Linked ListPage 1

Given the `head` of a singly linked list, return _the middle node of the linked list_.

If there are two middle nodes, return **the second middle** node.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/07/23/lc-midlist1.jpg)

<pre><code><strong>Input: head = [1,2,3,4,5]
</strong><strong>Output: [3,4,5]
</strong><strong>Explanation: The middle node of the list is node 3.
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/07/23/lc-midlist2.jpg)

<pre><code><strong>Input: head = [1,2,3,4,5,6]
</strong><strong>Output: [4,5,6]
</strong><strong>Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the list is in the range `[1, 100]`.
* `1 <= Node.val <= 100`

## Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:

        l = r = head

        while r and r.next :
            l = l.next
            r = r.next.next
        
        return l
```
