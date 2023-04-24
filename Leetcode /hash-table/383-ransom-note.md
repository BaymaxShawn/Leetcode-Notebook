---
description: easy
---

# 🥳 383 - Ransom Note

Given two strings `ransomNote` and `magazine`, return `true` _if_ `ransomNote` _can be constructed by using the letters from_ `magazine` _and_ `false` _otherwise_.

Each letter in `magazine` can only be used once in `ransomNote`.

&#x20;

**Example 1:**

<pre><code><strong>Input: ransomNote = "a", magazine = "b"
</strong><strong>Output: false
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: ransomNote = "aa", magazine = "ab"
</strong><strong>Output: false
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: ransomNote = "aa", magazine = "aab"
</strong><strong>Output: true
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= ransomNote.length, magazine.length <= 105`
* `ransomNote` and `magazine` consist of lowercase English letters.&#x20;

## Solution

题目要求我们判断一个字符串`ransomNote`是否可以通过另一个字符串`magazine`中的字母构建出来，且在构建`ransomNote`的过程中，不能重复使用`magazine`中的任何一个字母。

举个例子，假设`ransomNote`是字符串"apple"，`magazine`是字符串"aplepgonlmh"。那么我们可以从`magazine`中找到需要的字母来构建`ransomNote`，具体如下：

* 从`magazine`中选出一个"a"，并从`magazine`中删除这个"a"，现在`magazine`中剩余的字母是"plepgonlmh"；
* 从`magazine`中选出一个"p"，并从`magazine`中删除这个"p"，现在`magazine`中剩余的字母是"lepgonlmh"；
* 从`magazine`中选出一个"p"，但是发现`magazine`中已经没有"p"了，所以无法构建出"apple"，返回`False`。

换句话说，如果`magazine`中包含了`ransomNote`中所有的字母，并且每个字母都只使用了一次，那么就可以构建出`ransomNote`，返回`True`；否则返回`False`。

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:

        m = list(magazine)
        for i in ransomNote:
            if i in m:
                m.remove(i)
            else:
                return False
            
        return True
```
