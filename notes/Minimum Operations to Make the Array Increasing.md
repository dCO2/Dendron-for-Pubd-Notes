---
id: g0hedxejvzy9jso4b3zsggq
title: minimum operations to make the array increasing
desc: ''
updated: 1693478889263
created: 1693472915325
---

https://leetcode.com/problems/minimum-operations-to-make-the-array-increasing/

```
Input: nums = [1,1,1]
Output: 3
Input: nums = [1,5,2,4,1]
Output: 14
Input: nums = [8]
Output: 0
```

Initial wrong attempt:

```python
class Solution:
    def minOperations(self, nums: List[int]) -> int:
        n = len(nums)
        s = 0

        if n == 1: return 0

        for i in range(1, n):
            if nums[i] > nums[i-1]:
                continue
            else:
                s = i
                break
        
        ans = 0
        
        if s == 0:
            return ans
        else:
            prev = nums[s-1] + 1

        for i in range(s, n):
            ans += prev - nums[i]
            prev += 1
        
        return ans
```  


[[Minimum Replacements to Sort the Array]]  


<details>
<summary>Misc Problem Info</summary>

`Difficulty: Easy`  
`Tags:` [[ADP related to greedy]]

</details>
