---
title: 'Jump Game'
date: 2024-03-13T16:38:33-04:00
slug: 'jump-game'
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

### Jump game

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        goal = len(nums) - 1
        for i in range(len(nums)-1, -1, -1):
            if i + nums[i] >= goal:
                goal = i
        return goal == 0

        # @cache
        # def dfs(i):
        #     print(i)
        #     if i == len(nums)-1:
        #         return True
            
        #     for j in range(1, nums[i]+1):
        #         if dfs(i + j):
        #             return True
            
        #     return False
        
        # return dfs(0)
```