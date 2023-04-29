# 🍞 21 - Merge Two Sorted Lists

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return _the head of the merged linked list_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/03/merge\_ex1.jpg)

<pre><code><strong>Input: list1 = [1,2,4], list2 = [1,3,4]
</strong><strong>Output: [1,1,2,3,4,4]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: list1 = [], list2 = []
</strong><strong>Output: []
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: list1 = [], list2 = [0]
</strong><strong>Output: [0]
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in both lists is in the range `[0, 50]`.
* `-100 <= Node.val <= 100`
* Both `list1` and `list2` are sorted in **non-decreasing** order.

## Solution

#### dummy

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, list1, list2):
        """
        :type list1: Optional[ListNode]
        :type list2: Optional[ListNode]
        :rtype: Optional[ListNode]
        """

        curr = dummy = ListNode(0)

        while list1 and list2:
            if list1.val < list2.val:
                curr.next = list1
                list1 = list1.next
            else:
                curr.next = list2
                list2 = list2.next
            curr = curr.next
        curr.next = list1 or list2

        return dummy.next
```

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:

        dummy = head = ListNode(0)

        while list1 and list2:
            if list1.val <= list2.val:
                head.next = list1
                list1 = list1.next
            else:
                head.next = list2
                list2 = list2.next
            head = head.next
        head.next = list1 or list2

        return dummy.next
        
```

#### recrusion

```python
# Definition for singly-linked list.
# class ListNode:h
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:

        if list1 is None:
            return list2
        elif list2 is None:
            return list1
        elif list1.val < list2.val:
            head = list1
            list1 = list1.next
        else:
            head = list2
            list2 = list2.next
        
        head.next = self.mergeTwoLists(list1,list2)

        return head
```
