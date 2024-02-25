---
title: 'Sweep Line'
date: 2024-02-25T14:11:32-05:00
slug: 'sweep-line'
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

To find number of events occuring at a given point affected by multiple ranges.

### Problems

#### 370. Range Addition

- https://leetcode.com/problems/range-addition
- When event starts increase the value at the start position
- When it ends decrease the value at the end position

```python
starts = defaultdict(int)
ends = defaultdict(int)

for s, e, inc in updates:
    starts[s] += inc
    ends[e] += inc

inc = 0
res = []
for i in range(length):
    inc += starts[i]
    res.append(inc)
    inc -= ends[i]

return res
```

#### 2381. Shifting Letters II

- https://leetcode.com/problems/shifting-letters-ii/description/ 
