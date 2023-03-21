---
description: medium
---

# 🤜 19 - Remove Nth Node From End of List

Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/03/remove\_ex1.jpg)

<pre><code><strong>Input: head = [1,2,3,4,5], n = 2
</strong><strong>Output: [1,2,3,5]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: head = [1], n = 1
</strong><strong>Output: []
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: head = [1,2], n = 1
</strong><strong>Output: [1]
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the list is `sz`.
* `1 <= sz <= 30`
* `0 <= Node.val <= 100`
* `1 <= n <= sz`

## Solution

#### use dummy

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        
        slow = dummy = ListNode(0,head)
        fast = head

        while n >0 and fast:
            fast = fast.next
            n -= 1

        while fast:
            fast = fast.next
            slow = slow.next

        slow.next = slow.next.next

        return dummy.next

```

#### not dummy

```python
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        
        slow = fast = head

        while n >0 and fast:
            fast = fast.next
            n -= 1
        if not fast:
            return head.next

        while fast.next:
            fast = fast.next
            slow = slow.next

        slow.next = slow.next.next

        return head
```
