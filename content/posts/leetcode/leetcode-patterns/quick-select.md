---
title: 'Quick Select'
date: 2024-02-29T19:56:12-05:00
slug: 'quick-select'
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

- Select right as pivot element and left as fill position
- from left to right move elements smaller or equal to fill position and move the fill position to right
- Now p is the kth smallest element

```python
def quickselect(l, r):
  pivot = nums[r]
  p = l

  for i in range(l, r):
    if nums[i] <= pivot:
      nums[i], nums[p] = nums[p], nums[i]
      p += 1
    
  nums[p], nums[r] = nums[r], nums[p]

  if p > k:
    return quickselect(l, p-1)
  elif p < k:
    return quickselect(p+1, r)
  else:
    return nums[p]
```
