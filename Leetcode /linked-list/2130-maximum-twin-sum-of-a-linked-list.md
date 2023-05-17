# 😉 2130 - Maximum Twin Sum of a Linked List

In a linked list of size `n`, where `n` is **even**, the `ith` node (**0-indexed**) of the linked list is known as the **twin** of the `(n-1-i)th` node, if `0 <= i <= (n / 2) - 1`.

* For example, if `n = 4`, then node `0` is the twin of node `3`, and node `1` is the twin of node `2`. These are the only nodes with twins for `n = 4`.

The **twin sum** is defined as the sum of a node and its twin.

Given the `head` of a linked list with even length, return _the **maximum twin sum** of the linked list_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/12/03/eg1drawio.png)

<pre><code><strong>Input: head = [5,4,2,1]
</strong><strong>Output: 6
</strong><strong>Explanation:
</strong>Nodes 0 and 1 are the twins of nodes 3 and 2, respectively. All have twin sum = 6.
There are no other nodes with twins in the linked list.
Thus, the maximum twin sum of the linked list is 6. 
</code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/12/03/eg2drawio.png)

<pre><code><strong>Input: head = [4,2,2,3]
</strong><strong>Output: 7
</strong><strong>Explanation:
</strong>The nodes with twins present in this linked list are:
- Node 0 is the twin of node 3 having a twin sum of 4 + 3 = 7.
- Node 1 is the twin of node 2 having a twin sum of 2 + 2 = 4.
Thus, the maximum twin sum of the linked list is max(7, 4) = 7. 
</code></pre>

**Example 3:**

![](https://assets.leetcode.com/uploads/2021/12/03/eg3drawio.png)

<pre><code><strong>Input: head = [1,100000]
</strong><strong>Output: 100001
</strong><strong>Explanation:
</strong>There is only one node with a twin in the linked list having twin sum of 1 + 100000 = 100001.
</code></pre>

&#x20;

**Constraints:**

* The number of nodes in the list is an **even** integer in the range `[2, 105]`.
* `1 <= Node.val <= 105`

## Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def pairSum(self, head: Optional[ListNode]) -> int:
        cur = head
        value = []

        while cur:
            value.append(cur.val)
            cur = cur.next

        i = 0
        j = len(value)-1
        max_sum = -inf
        while i<j:
            max_sum = max(max_sum,value[i]+value[j])
            i += 1
            j -= 1
        return max_sum
```
