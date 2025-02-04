---
title: 'Tree'
date: 2024-02-29T15:36:29-05:00
slug: 'tree'
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


### Problems

#### 2385. Amount of Time for Binary Tree to Be Infected

- https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/

```python
self.maxDistance = 0
def dfs(node):
    depth = 0
    if not node:
        return depth
    leftDepth = dfs(node.left)
    rightDepth = dfs(node.right)
    if node.val == start:
        self.maxDistance = max(leftDepth, rightDepth)
        depth = -1
    elif leftDepth >= 0 and rightDepth >= 0:
        depth = max(leftDepth, rightDepth) + 1
    else:
        distance = abs(leftDepth) + abs(rightDepth)
        self.maxDistance = max(self.maxDistance, distance)
        depth = min(leftDepth, rightDepth) - 1
    return depth
dfs(root)
return self.maxDistance
```
