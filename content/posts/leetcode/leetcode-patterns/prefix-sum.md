---
title: 'Prefix Sum'
date: 2025-04-24T20:43:12-07:00
slug: 'prefix-sum'
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

- Prefix[i] will have value calculated till ith index.


**Subarray sum equals k**

```python
res = 0
presumToCount = defaultdict(int)
presum = 0
for num in nums:
    presum += num
    if presum == k:
        res += 1
    res += presumToCount[presum - k]
    presumToCount[presum] += 1
return res
```

## Problems

- [2845. Count of Interesting Subarrays](/posts/leetcode/leetcode-daily/count-of-interesting-subarrays/)
- [1915. Number of Wonderful Substrings](https://leetcode.com/problems/number-of-wonderful-substrings/description/)
    - Similar to sub array sum equals k, but we use bitmask and xor operations on the prefix values to find the substrings with zero odd count (prefix is zero) and with 1 odd count.