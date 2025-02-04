---
title: 'SPFA (Shortest Path Faster Algorithm)'
date: 2024-02-23T15:35:51-05:00
slug: 'spfa'
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

dist = [inf] * (n+1)
dist[src] = 0
q = deque()
q.append(src)
visited = set()
visited.add(src)
while q:
    u = q.popleft()
    visited.remove(u)

    for v, d in adj[u]:
        if dist[u] + d < dist[v]:
            if v not in visited:
                q.append(v)
                visited.add(v)
            dist[v] = dist[u] + d
```

