---
title: 'Sqrt Decomposition'
date: 2024-03-19T15:37:14-04:00
slug: 'sqrt-decomposition'
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

```python
class NumArray:

    def __init__(self, nums: List[int]):
        self.nums = nums
        self.n = len(nums)
        self.k = int(sqrt(self.n))
        self.dp = [0] * ((self.n //self. k)+1)
        for i in range(self.n):
            self.dp[i//self.k] += self.nums[i]

    def sumRange(self, left: int, right: int) -> int:
        s = 0
        while left < right and left % self.k != 0 and left != 0:
            s += self.nums[left]
            left += 1
        
        while left + self.k - 1 < right:
            s += self.dp[left//self.k]
            left += self.k
        
        while left <= right:
            s += self.nums[left]
            left += 1
        
        return s


# Your NumArray object will be instantiated and called as such:
# obj = NumArray(nums)
# param_1 = obj.sumRange(left,right)
```