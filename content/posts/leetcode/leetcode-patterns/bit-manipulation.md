---
title: 'Bit Manipulation'
date: 2024-03-10T19:35:59-04:00
slug: 'bit-manipulation'
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

### Generating bitmask

```
n = len(nums)
nth_bit = 1 << n
for i in range(2**n):
    bitmask = bin(i | nth_bit)[3:]
    print(bitmask)

n = len(nums)
for i in range(2**n, 2**(n+1)):
    bitmask = bin(i)[3:]
    print(bitmask)
```