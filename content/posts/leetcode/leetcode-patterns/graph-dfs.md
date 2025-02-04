---
title: 'Graph DFS'
date: 2024-02-28T13:45:35-05:00
slug: 'graph-dfs'
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
visited = set()
def dfs(u):
    if u == destination:
        return True
    
    if u in visited:
        return False
    
    visited.add(u)
    
    for v in adj[u]:
        if (dfs(v)):
            return True
    
    return False

return dfs(source)
```

```python
stack = [source]
visited = set()
while stack:
    u = stack.pop()
    
    if u == destination:
        return True
    
    if u in visited:
        continue
    
    visited.add(u)
    
    for v in adj[u]:
        stack.append(v)

return False
```

### Problems

#### 332. Reconstruct Itinerary

- https://leetcode.com/problems/reconstruct-itinerary/description/
- Eulerian path

```python
adj = defaultdict(list)
for u, v in tickets:
    adj[u].append(v)

for u, nei in adj.items():
    nei.sort(reverse=True)

res = []
def dfs(u):
    nonlocal res
    while adj[u]:
        nxt = adj[u].pop()
        dfs(nxt)
    res.append(u)
dfs('JFK')
return res[::-1]
```

#### 1059. All Paths from Source Lead to Destination

- https://leetcode.com/problems/all-paths-from-source-lead-to-destination/description/
- Cycle detection
- if a node leads to destination then all the nodes connecting to this node reaches the destination we can use this solution.

```python
adj = defaultdict(list)
for u, v in edges:
    adj[u].append(v)

white, gray, black = 0, 1, 2
colors = [white] * n
def dfs(u):
    nonlocal white, gray, black

    if colors[u] == black:
        return True

    if colors[u] == gray:
        # loop
        return False

    if not adj[u]:
        # leaf
        return u == destination

    colors[u] = gray
    for v in adj[u]:
        ret = dfs(v)
        if not ret:
            return False
    colors[u] = black
    return True
    
return dfs(source)
```