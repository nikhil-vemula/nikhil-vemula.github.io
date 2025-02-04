---
title: 'Combination Sum'
date: 2024-03-12T17:44:52-04:00
slug: 'comb-sum'
tags: []
author: "Me"
showToc: false
TocOpen: false
draft: false
hidemeta: false
comments: true
description: ""
canonicalURL: ""
disableHLJS: false
disableShare: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
---
### Combination Sum

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        
        res = []
        comb = []
        def backtrack(start, s):
            if s > target:
                return
            
            if s == target:
                res.append(comb[:])
                return
            
            for i in range(start, len(candidates)):
                comb.append(candidates[i])
                backtrack(i, s + candidates[i])
                comb.pop()


        backtrack(0, 0)
        return res
```

### Combination Sum II

```python {linenos=inline,hl_lines=[15,16, 18]}
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        candidates.sort()
        res = []
        comb = []
        def backtrack(start, s):
            if s > target:
                return
            
            if s == target:
                res.append(comb[:])
                return

            for i in range(start, len(candidates)):
                if i > start and candidates[i-1] == candidates[i]:
                    continue
                comb.append(candidates[i])
                backtrack(i+1, s + candidates[i])
                comb.pop()
        
        backtrack(0, 0)
        return res
```

### Combination Sum III

```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        res = []
        comb = []
        def backtrack(s, nxt):
            if s == 0 and len(comb) == k:
                res.append(comb[:])
                return
            
            if s < 0 or len(comb) == k:
                return
            
            for i in range(nxt, 10):
                comb.append(i)
                backtrack(s-i, i+1)
                comb.pop()
            
        backtrack(n, 1)
        return res
```

### Combinatio Sum IV

```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        dp = [0] * (target+1)
        dp[0] = 1
        for i in range(target+1):
            for num in nums:
                if i - num < 0:
                    continue

                dp[i] += dp[i-num]
        return dp[-1]
        
        # @cache
        # def backtrack(s):
        #     if s == target:
        #         return 1
            
        #     if s > target:
        #         return 0
            
        #     res = 0
        #     for num in nums:
        #         res += backtrack(s+num)
        #     return res
        
        # return backtrack(0)
```
