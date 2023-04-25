---
description: easy
---

# 😍 141 - Linked List Cycle

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

<pre><code><strong>Input: head = [3,2,0,-4], pos = 1
</strong><strong>Output: true
</strong><strong>Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist\_test2.png)

<pre><code><strong>Input: head = [1,2], pos = 0
</strong><strong>Output: true
</strong><strong>Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.
</strong></code></pre>

**Example 3:**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist\_test3.png)

<pre><code><strong>Input: head = [1], pos = -1
</strong><strong>Output: false
</strong><strong>Explanation: There is no cycle in the linked list.
</strong></code></pre>

&#x20;

**Constraints:**

* The number of the nodes in the list is in the range `[0, 104]`.
* `-105 <= Node.val <= 105`
* `pos` is `-1` or a **valid index** in the linked-list.

**Follow up:** Can you solve it using `O(1)` (i.e. constant) memory?

## Solution

[https://www.youtube.com/watch?v=gBTe7lFR3vc](https://www.youtube.com/watch?v=gBTe7lFR3vc)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        
        slow = fast = head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if fast == slow:
                return True
        
        return False
```
