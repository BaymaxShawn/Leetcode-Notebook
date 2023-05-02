---
description: easy
---

# 😛 125 - Valid Palindrome

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "A man, a plan, a canal: Panama"
</strong><strong>Output: true
</strong><strong>Explanation: "amanaplanacanalpanama" is a palindrome.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "race a car"
</strong><strong>Output: false
</strong><strong>Explanation: "raceacar" is not a palindrome.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: s = " "
</strong><strong>Output: true
</strong><strong>Explanation: s is an empty string "" after removing non-alphanumeric characters.
</strong>Since an empty string reads the same forward and backward, it is a palindrome.
</code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 2 * 105`
* `s` consists only of printable ASCII characters.

## Solution

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        res = ''
        for i in s:
            if i.isalnum():
                res += i.lower()
        print(res)
        
        l,r = 0,len(res)-1
        while l<r:
            if res[l] != res[r]:
                return False
            l += 1
            r -= 1
        return True
    
```

#### Hits:

`isalnum()` 是 Python 字符串对象中的一个方法，用于判断一个字符串是否由字母或数字组成，如果是，则返回 True，否则返回 False。具体来说，该方法会遍历字符串中的每个字符，如果所有字符都是字母或数字，则返回 True，否则返回 False。该方法的语法如下：

```python
pythonCopy codestr.isalnum()
```

其中，`str` 是一个字符串对象。下面是一个简单的示例：

```python
pythonCopy codes1 = "hello123"
s2 = "hello!123"
print(s1.isalnum())  # True
print(s2.isalnum())  # False
```

在上述代码中，我们定义了两个字符串 `s1` 和 `s2`，并分别调用它们的 `isalnum()` 方法。由于 `s1` 由字母和数字组成，而 `s2` 中包含了一个非字母和数字的字符，因此 `s1.isalnum()` 返回 True，而 `s2.isalnum()` 返回 False。

需要注意的是，空字符串 `""` 虽然不包含字母和数字，但也会被 `isalnum()` 方法认为是由字母和数字组成的，因此它的返回值也是 True。
