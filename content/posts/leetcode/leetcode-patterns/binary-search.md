---
title: 'Binary Search'
date: 2024-03-01T11:14:58-05:00
slug: 'binary-search'
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

- Choose the left value
- Choose the right value
- Binary search from left to right

```python
left = 0
right = len(nums)
while left < right:
    mid = (left + right) // 2
    if nums[mid] > target: # This condition can be changed according to the problem
        right = mid
    else:
        left = mid+1


if left > 0 and nums[left-1] == target:
    return left-1

return -1
```

### Problems

#### 1011. Capacity To Ship Packages Within D Days

- https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/
