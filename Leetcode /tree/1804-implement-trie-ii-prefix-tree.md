# 👺 1804 - Implement Trie II (Prefix Tree)

```python
class Trie:

    def __init__(self):
        self.count = 0 
        self.tree = {}

    def insert(self, word: str) -> None:
        for w in word:
            if w not in self.tree:
                self.tree[w] = Trie()
            self = self.tree[w]
        self.count += 1
        

    def countWordsEqualTo(self, word: str) -> int:
        for w in word:
            if w not in self.tree:
                return 0
            self = self.tree[w]
        return self.count
        

    def countWordsStartingWith(self, prefix: str) -> int:
        for i in prefix:
            if i not in self.tree:
                return 0
            self = self.tree[i]
        
        res = self.count

        for key in self.tree:
            res += self.countWordsStartingWith(key)
        
        return res

    def erase(self, word: str) -> None:
        for w in word:
            self = self.tree[w]
        
        self.count -=1


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.countWordsEqualTo(word)
# param_3 = obj.countWordsStartingWith(prefix)
# obj.erase(word)
```
