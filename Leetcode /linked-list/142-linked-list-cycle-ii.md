# 😇 142 - Linked List Cycle II

Given the `head` of a linked list, return _the node where the cycle begins. If there is no cycle, return_ `null`.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to (**0-indexed**). It is `-1` if there is no cycle. **Note that** `pos` **is not passed as a parameter**.

**Do not modify** the linked list.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

<pre><code><strong>Input: head = [3,2,0,-4], pos = 1
</strong><strong>Output: tail connects to node index 1
</strong><strong>Explanation: There is a cycle in the linked list, where tail connects to the second node.
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist\_test2.png)

<pre><code><strong>Input: head = [1,2], pos = 0
</strong><strong>Output: tail connects to node index 0
</strong><strong>Explanation: There is a cycle in the linked list, where tail connects to the first node.
</strong></code></pre>

**Example 3:**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist\_test3.png)

<pre><code><strong>Input: head = [1], pos = -1
</strong><strong>Output: no cycle
</strong><strong>Explanation: There is no cycle in the linked list.
</strong></code></pre>

&#x20;

**Constraints:**

* The number of the nodes in the list is in the range `[0, 104]`.
* `-105 <= Node.val <= 105`
* `pos` is `-1` or a **valid index** in the linked-list.

## Solution

[https://www.bilibili.com/video/BV1if4y1d7ob/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810](https://www.bilibili.com/video/BV1if4y1d7ob/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:

        fast = slow = head

        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next

            if fast == slow:
                idx1 = fast
                idx2 = head
                while idx1 != idx2:
                    idx1 = idx1.next
                    idx2 = idx2.next
                
                return idx1
```

链表中的环有时可以用来解决一些问题，比如：

1. 判断链表是否有环：使用快慢指针的方法，如果两个指针在遍历过程中相遇，那么就可以判断出链表中有环。
2. 判断环的长度：从相遇的点出发，继续走，直到回到这个点，走的步数就是环的长度。
3. 找到环的起点：使用快慢指针的方法，相遇的点距离环的起点的距离和链表头节点距离环的起点的距离相等，因此可以从相遇的点和头节点同时出发，每次走一步，相遇的点就是环的起点。

举个例子，比如一个公司有n个员工，员工的编号分别是1, 2, ..., n。每个员工有一个上级，除了老板没有上级，其他员工有且只有一个上级。这些员工的关系可以用一个链表表示，链表中的每个节点表示一个员工，节点中存储员工的编号和其上级的指针。如果链表中存在环，说明公司中存在上下级关系不合理的情况，需要解决。通过找到环的起点，可以找到上下级关系出现问题的地方，进行调整。
