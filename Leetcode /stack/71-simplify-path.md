---
description: medium
---

# 🥲 71 -  Simplify Path

Given a string `path`, which is an **absolute path** (starting with a slash `'/'`) to a file or directory in a Unix-style file system, convert it to the simplified **canonical path**.

In a Unix-style file system, a period `'.'` refers to the current directory, a double period `'..'` refers to the directory up a level, and any multiple consecutive slashes (i.e. `'//'`) are treated as a single slash `'/'`. For this problem, any other format of periods such as `'...'` are treated as file/directory names.

The **canonical path** should have the following format:

* The path starts with a single slash `'/'`.
* Any two directories are separated by a single slash `'/'`.
* The path does not end with a trailing `'/'`.
* The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period `'.'` or double period `'..'`)

Return _the simplified **canonical path**_.

&#x20;

**Example 1:**

<pre><code><strong>Input: path = "/home/"
</strong><strong>Output: "/home"
</strong><strong>Explanation: Note that there is no trailing slash after the last directory name.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: path = "/../"
</strong><strong>Output: "/"
</strong><strong>Explanation: Going one level up from the root directory is a no-op, as the root level is the highest level you can go.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: path = "/home//foo/"
</strong><strong>Output: "/home/foo"
</strong><strong>Explanation: In the canonical path, multiple consecutive slashes are replaced by a single one.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= path.length <= 3000`
* `path` consists of English letters, digits, period `'.'`, slash `'/'` or `'_'`.
* `path` is a valid absolute Unix path.

## Solution

#### stack

```python
class Solution:
    def simplifyPath(self, path: str) -> str:

        stack = []

        for i in path.split("/"):
            if i == "..":
                if stack:
                    stack.pop()
            elif i == "." or not i:
                continue
            else:
                stack.append(i)
            
        res = "/"+"/".join(stack)

        return res
```
