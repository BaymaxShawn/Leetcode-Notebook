# 😁 1290 - Convert Binary Number in a Linked List to Integer

Given `head` which is a reference node to a singly-linked list. The value of each node in the linked list is either `0` or `1`. The linked list holds the binary representation of a number.

Return the _decimal value_ of the number in the linked list.

The **most significant bit** is at the head of the linked list.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/12/05/graph-1.png)

<pre><code><strong>Input: head = [1,0,1]
</strong><strong>Output: 5
</strong><strong>Explanation: (101) in base 2 = (5) in base 10
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: head = [0]
</strong><strong>Output: 0
</strong></code></pre>

&#x20;

**Constraints:**

* The Linked List is not empty.
* Number of nodes will not exceed `30`.
* Each node's value is either `0` or `1`.

## Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def getDecimalValue(self, head: ListNode) -> int:
      num = head.val
      while head.next:
        num = num*2 + head.next.val 
        head = head.next

      return num
```
