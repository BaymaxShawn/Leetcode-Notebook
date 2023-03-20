---
description: medium 2023/03/19 每日一题
---

# 😅 211 - Design Add and Search Words Data Structure

Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the `WordDictionary` class:

* `WordDictionary()` Initializes the object.
* `void addWord(word)` Adds `word` to the data structure, it can be matched later.
* `bool search(word)` Returns `true` if there is any string in the data structure that matches `word` or `false` otherwise. `word` may contain dots `'.'` where dots can be matched with any letter.

&#x20;

**Example:**

<pre><code><strong>Input
</strong>["WordDictionary","addWord","addWord","addWord","search","search","search","search"]
[[],["bad"],["dad"],["mad"],["pad"],["bad"],[".ad"],["b.."]]
<strong>Output
</strong>[null,null,null,null,false,true,true,true]

<strong>Explanation
</strong>WordDictionary wordDictionary = new WordDictionary();
wordDictionary.addWord("bad");
wordDictionary.addWord("dad");
wordDictionary.addWord("mad");
wordDictionary.search("pad"); // return False
wordDictionary.search("bad"); // return True
wordDictionary.search(".ad"); // return True
wordDictionary.search("b.."); // return True
</code></pre>

&#x20;

**Constraints:**

* `1 <= word.length <= 25`
* `word` in `addWord` consists of lowercase English letters.
* `word` in `search` consist of `'.'` or lowercase English letters.
* There will be at most `3` dots in `word` for `search` queries.
* At most `104` calls will be made to `addWord` and `search`.

## Solution

#### Brute Force&#x20;

$$O(M⋅N)$$ time complexity for the search

```python
class WordDictionary:
    def __init__(self):
        self.d = defaultdict(set)

    def addWord(self, word: str) -> None:
        self.d[len(word)].add(word)

    def search(self, word: str) -> bool:
        m = len(word)
        for w in self.d[m]:
            i = 0
            while i<m and (w[i] == word[i] or word[i] == "."):
                i += 1
            if i == m :
                return True
        return False
            
```

这段代码使用了 Python 内置的 defaultdict 类型。defaultdict 可以自动初始化字典中不存在的键值，从而避免了在使用字典时频繁使用 if 判断键值是否存在的操作。

在这个例子中，定义了一个空的 defaultdict 对象 self.d，其中每个键的值是一个 set 集合。这里的 defaultdict(set) 意味着当我们第一次给一个新的键赋值时，它的值将被初始化为一个空的 set 集合。而且，因为 defaultdict 的特性，我们不需要再去判断键是否存在了。

可以通过以下方式向 defaultdict 中添加键值对：

```python
pythonCopy codeself.d[key].add(value)
```

如果 key 在 self.d 中不存在，则自动为 key 创建一个 set 集合，并向该集合中添加 value。如果 key 已经存在，则只向对应的集合中添加 value。

#### Tire

```python

class WordDictionary:
    def __init__(self):
        self.trie = {}

    def addWord(self, word: str) -> None:
        node = self.trie
        for c in word:
            if c not in node:
                node[c] = {}
            node = node[c] 
        node['$'] = True
        #node['$']就是结尾了

    def search(self, word: str) -> bool:
        def search_in_node(word, node) -> bool:
            for i, c in enumerate(word):
                if c not in node:
                    if c == '.':
                        for x in node:
                            if x!= '$' and search_in_node(word[i+1:],node[x]):
                                return True
                    return False
                else:
                    node = node[c]
            return '$' in node

        return search_in_node(word,self.trie)



```



