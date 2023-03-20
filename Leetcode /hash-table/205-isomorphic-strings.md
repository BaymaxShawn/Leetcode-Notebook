# 🤪 205 - Isomorphic Strings

Given two strings `s` and `t`, _determine if they are isomorphic_.

Two strings `s` and `t` are isomorphic if the characters in `s` can be replaced to get `t`.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "egg", t = "add"
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "foo", t = "bar"
</strong><strong>Output: false
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: s = "paper", t = "title"
</strong><strong>Output: true
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 5 * 104`
* `t.length == s.length`
* `s` and `t` consist of any valid ascii character.



## Solution

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:

        return len(set(zip(s,t))) == len(set(s)) == len(set(t))

        
```

`zip` 是 Python 中一个内置的函数，它用于将多个可迭代对象打包成元组的迭代器，返回一个可迭代对象。

例如，假设有两个列表 `a = [1, 2, 3]` 和 `b = [4, 5, 6]`，可以使用 `zip` 将它们打包成元组的迭代器：

```python
pythonCopy code>>> zipped = zip(a, b)
>>> zipped
<zip object at 0x7fa6fc0e6e80>
```

使用 `list` 函数可以将迭代器转换为列表：

```scss
scssCopy code>>> list(zipped)
[(1, 4), (2, 5), (3, 6)]
```

在上面的代码中，`zip` 会返回一个迭代器，它包含了元组 `(a[0], b[0])`、`(a[1], b[1])` 和 `(a[2], b[2])`。在 `for` 循环中使用 `zip` 可以同时迭代两个或多个列表。

\
