# 🤏 443 - String Compression

Given an array of characters `chars`, compress it using the following algorithm:

Begin with an empty string `s`. For each group of **consecutive repeating characters** in `chars`:

* If the group's length is `1`, append the character to `s`.
* Otherwise, append the character followed by the group's length.

The compressed string `s` **should not be returned separately**, but instead, be stored **in the input character array `chars`**. Note that group lengths that are `10` or longer will be split into multiple characters in `chars`.

After you are done **modifying the input array,** return _the new length of the array_.

You must write an algorithm that uses only constant extra space.

&#x20;

**Example 1:**

<pre><code><strong>Input: chars = ["a","a","b","b","c","c","c"]
</strong><strong>Output: Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]
</strong><strong>Explanation: The groups are "aa", "bb", and "ccc". This compresses to "a2b2c3".
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: chars = ["a"]
</strong><strong>Output: Return 1, and the first character of the input array should be: ["a"]
</strong><strong>Explanation: The only group is "a", which remains uncompressed since it's a single character.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]
</strong><strong>Output: Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].
</strong><strong>Explanation: The groups are "a" and "bbbbbbbbbbbb". This compresses to "ab12".
</strong></code></pre>

## Solution

#### Python

```python
class Solution(object):
    def compress(self, chars):
        """
        :type chars: List[str]
        :rtype: int
        """

        if not chars:
            return 0

        idx = 0
        count = 1 
        for i in range(1,len(chars)):
            if chars[i] == chars[i-1]:
                count +=1
            else:
                chars[idx] = chars[i-1]
                idx +=1
                if count > 1:
                    constr = str(count)
                    for j in range(len(constr)):
                        chars[idx] = constr[j]
                        idx +=1
                count = 1
            
        chars[idx] = chars[-1]
        idx += 1
        if count > 1:
            constr = str(count)
            for j in range(len(constr)):
                chars[idx] = constr[j]
                idx +=1
        
        return idx
```
