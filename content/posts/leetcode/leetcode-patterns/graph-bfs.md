---
title: 'Graph BFS'
date: 2024-02-24T11:55:30-05:00
slug: 'graph-bfs'
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
q = deque()
q.append(start)
visited = set()
visited.add(start)
while q:
    u = q.popleft()

    for v in adj[u]:
        if v not in visited:
            visited.add(v)
            q.append(v)
```

### Problems

#### 2092. Find All People With Secret
- https://leetcode.com/problems/find-all-people-with-secret
- Revisit the node based if the secret is know to that node earliest. Revisit the node if better option is found in the later point.
- Multi source bfs revisiting the nodes if better option is found.

```python {linenos=inline,hl_lines=[10]}
q = deque()
q.append([0, 0])
q.append([0, firstPerson])
earliest = [inf] *  n
earliest[0] = 0
earliest[firstPerson] = 0
while q:
    time, u = q.popleft()
    for t, v in adj[u]:
        if t >= time and t < earliest[v]:
            earliest[v] = t
            q.append([t, v])
```