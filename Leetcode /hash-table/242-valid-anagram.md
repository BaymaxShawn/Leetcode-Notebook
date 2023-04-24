---
description: easy
---

# 😁 242 - Valid Anagram

Given two strings `s` and `t`, return `true` _if_ `t` _is an anagram of_ `s`_, and_ `false` _otherwise_.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "anagram", t = "nagaram"
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "rat", t = "car"
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length, t.length <= 5 * 104`
* `s` and `t` consist of lowercase English letters.

## Solution

#### method 1

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:

        if len(s) != len(t):
            return False

        hashtable = {}

        for i in s:
            if i not in hashtable:
                hashtable[i] = 1
            else: 
                hashtable[i] += 1
            
        for j in t:
            if j in hashtable:
                hashtable[j] -= 1
            else:
                return False
        
        for char in hashtable:
            if hashtable[char] != 0:
                return False
        return True
```

#### method 2

`collections.Counter(s)` 是一个 Python 中的计数器（Counter）对象，用于统计一个可迭代对象中各个元素出现的次数。在这里，传入的可迭代对象是字符串 `s`，则 `collections.Counter(s)` 返回一个字典，其中字典的键是字符串 `s` 中出现的每个字符，对应的值是该字符出现的次数。

例如，对于字符串 `s = "hello"`，`collections.Counter(s)` 返回的字典是 `{'h': 1, 'e': 1, 'l': 2, 'o': 1}`，表示字符 `'h'` 出现了 1 次，字符 `'e'` 出现了 1 次，字符 `'l'` 出现了 2 次，字符 `'o'` 出现了 1 次。

`collections.Counter(s)` 是 Python 标准库 `collections` 模块中的一个类，可以使用 `from collections import Counter` 来导入该类。可以使用计数器对象的多个方法，如 `most_common()` 方法返回出现次数最多的前几个元素，也可以使用 `+` 或 `-` 运算符将计数器对象进行合并或减法操作等。

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:

        return Counter(s) == Counter(t)
```

\
