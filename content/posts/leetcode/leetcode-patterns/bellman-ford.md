---
title: 'Bellman Ford'
date: 2024-02-23T15:32:54-05:00
slug: 'bellman-ford'
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
# O(V*E)
dist = [inf] * n
dist[src] = 0
for i in range(n-1):
    changed = False
    for u, v, d in edges:
        if dist[u] + d < dist[v]:
            dist[v] =  dist[u] + d
            changed = True
    if not changed:
        break
```

### Problems

### 787. Cheapest Flights Within K Stops

- https://leetcode.com/problems/cheapest-flights-within-k-stops
- Apply bellman ford for `k+1` iterations

