# 🖥 206 - Reverse Linked List

Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)

<pre><code><strong>Input: head = [1,2,3,4,5]
</strong><strong>Output: [5,4,3,2,1]
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg)

<pre><code><strong>Input: head = [1,2]
</strong><strong>Output: [2,1]
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: head = []
</strong><strong>Output: []
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the list is the range `[0, 5000]`.
* `-5000 <= Node.val <= 5000`

## Solution

#### recursive

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:

        if not head or not head.next:
            return head
        
        res = self.reverseList(head.next)
        head.next.next = head
       
        head.next = None

        return res
        
```

#### Iterative

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:

        l = None
        r = head
        while r:
            next_temp = r.next
            r.next = l
            l = r
            r = next_temp
            
        return l
        
```

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        dummy = None

        while head:
            cur = head.next
            head.next = dummy
            dummy = head 
            head = cur
        
        return dummy
```

dummy 顶替了head，但head不存在了，所以return dummy
