# 🌊 208 - Implement Trie (Prefix Tree)

A [**trie**](https://en.wikipedia.org/wiki/Trie) (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

* `Trie()` Initializes the trie object.
* `void insert(String word)` Inserts the string `word` into the trie.
* `boolean search(String word)` Returns `true` if the string `word` is in the trie (i.e., was inserted before), and `false` otherwise.
* `boolean startsWith(String prefix)` Returns `true` if there is a previously inserted string `word` that has the prefix `prefix`, and `false` otherwise.

&#x20;

**Example 1:**

<pre><code><strong>Input
</strong>["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
<strong>Output
</strong>[null, null, true, false, true, null, true]

<strong>Explanation
</strong>Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // return True
trie.search("app");     // return False
trie.startsWith("app"); // return True
trie.insert("app");
trie.search("app");     // return True
</code></pre>

&#x20;

**Constraints:**

* `1 <= word.length, prefix.length <= 2000`
* `word` and `prefix` consist only of lowercase English letters.
* At most `3 * 104` calls **in total** will be made to `insert`, `search`, and `startsWith`.

## Solution

[https://www.youtube.com/watch?v=nKlb8JWYBQk](https://www.youtube.com/watch?v=nKlb8JWYBQk)

Tire Tree

```python
class TrieNode:
    def __init__(self,char):
        self.char = char
        self.children = {}
        self.is_last = False

class Trie:
    
    def __init__(self):
        self.trie = TrieNode("#")

    def insert(self, word: str) -> None:
        root = self.trie

        for char in word:
            if char not in root.children:
                root.children[char] = TrieNode(char)

            root = root.children[char]

        root.is_last = True

    def search(self, word: str) -> bool:
        root = self.trie

        for char in word:
            if char in root.children:
                root = root.children[char]
            else:
                return False
        
        return root.is_last

    def startsWith(self, prefix: str) -> bool:
        root = self.trie

        for char in prefix:
            if char in root.children:
                 root = root.children[char]
            else:
                return False
        
        return True
        
```
