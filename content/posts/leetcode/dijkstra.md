---
title: 'Dijkstra'
date: 2024-02-23T15:22:08-05:00
slug: 'dijkstra'
tags: ['leetcode']
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

## Dijkstra's

```python
# O(V + E*log(V))
dist = [inf] * (n)
dist[src] = 0
mi_heap = [[0, src]]
visited = set()
while mi_heap:
    dist, u = heappop(mi_heap)
    visited.add(u)
    for v, t in adj[u]:
        if v in visited:
            continue
        if dist[u] + t < dist[v]:
            dist[v] = dist[u] + t
            heappush(mi_heap, [dist[v], v])
```

### Problems

#### 743. Network Delay Time

- https://leetcode.com/problems/network-delay-time/
- Apply dijkstra's algorithm to get the shortest times from source node

#### 1631. Path With Minimum Effort

- https://leetcode.com/problems/path-with-minimum-effort/
- 2D verion of dijkstra's, and instead of the adding the distance from the previous node we do maximum of the previous node when comparing

```python {linenos=inline,hl_lines=[17]}
dirs = [[0, 1], [1, 0], [0, -1], [-1, 0]]
rows, cols = len(heights), len(heights[0])

dp = [[inf for _ in range(cols)] for _ in range(rows)]
dp[0][0] = 0
mi_heap = [[0, 0, 0]]
visited = set()
while mi_heap:
    d, x, y = heappop(mi_heap)

    visited.add((x, y))

    for d1, d2 in dirs:
        adj_x = x + d1
        adj_y = y + d2
        if 0 <= adj_x < rows and 0 <= adj_y < cols and (adj_x, adj_y) not in visited:
            mx_diff = max(dp[x][y], abs(heights[adj_x][adj_y] - heights[x][y]))
            if dp[adj_x][adj_y] > mx_diff:
                dp[adj_x][adj_y] = mx_diff
                heappush(mi_heap, [mx_diff, adj_x, adj_y])

return dp[-1][-1]
```