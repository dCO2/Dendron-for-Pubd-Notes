---
id: pzmeyqwtht28awfevtqczkd
title: thinking non-intuitively about recursion
desc: ''
updated: 1691665844518
created: 1687174813673
---

A good example? https://leetcode.com/problems/letter-combinations-of-a-phone-number/

A top-down approach to thinking about recursion:  
"Solutions" are built from the big-level tasks and integrated with the small-level tasks. This way, the solutions can be passed from the big-level tasks to the small-level tasks through the paramaters in the recursive function call. As shown in this solution to the _Letter Combinations Of a Phone Number_ problem.
  
  
```python
ans = []
d = {}
d["2"] = ["a","b","c"]
...
...

def backtrack(i, curstr):
    if len(curstr) == len(digits):
        ans.append(curstr)
        return

    for ch in d[digits[i]]:
      backtrack(i+1, curstr + ch)

```  
  
A bottom-up solution to this problem can also be implemented. Here, the solution is returned (AS AN ARRAY) from the small-level tasks and integrated into a solution from a big-level tasks.

In the _Validate Binary Search Tree_ problem, the parameters passed (top-down) from the big-level tasks to the small-level tasks are (minValLeft & maxValRight) which is used to compute the small-level tasks. Here on the other hand, the "final solution" is a boolean which is basically the AND of all the intermediate small-level tasks/solution. Therefore, if any one small-level task/solution/validity fails, everything (the big-level solution(s)) fail(s).

```python

def isValidBST(self, root: Optional[TreeNode]) -> bool:

    def caller(node, mnleft, mxright):
        if not node:
            return True

        if not (node.val < mxright and node.val > mnleft):
            return False

        return (caller(node.left, mnleft, node.val) and
                caller(node.right, node.val, mxright))
    
    return caller(root, float("-inf"), float("inf"))

```
