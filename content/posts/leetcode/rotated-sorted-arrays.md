---
title: 'Rotated Arrays'
date: 2024-03-14T19:48:37-04:00
slug: 'rotated-sorted-arrays'
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

### Min in rotated sorted array

```python
left = 0
right = len(nums)-1
while left < right:
    if nums[left] < nums[right]:
        return nums[left]
    
    mid = (left + right) // 2
    if nums[mid] < nums[right]:
        right = mid
    else:
        left = mid + 1

return nums[left]
```