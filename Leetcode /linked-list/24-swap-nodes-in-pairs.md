# 😆 24 - Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/03/swap\_ex1.jpg)

<pre><code><strong>Input: head = [1,2,3,4]
</strong><strong>Output: [2,1,4,3]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: head = []
</strong><strong>Output: []
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: head = [1]
</strong><strong>Output: [1]
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the list is in the range `[0, 100]`.
* `0 <= Node.val <= 100`

## Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next:
            return head

        first = head
        second = head.next

        first.next = self.swapPairs(second.next)
        second.next = first

        return second

```
