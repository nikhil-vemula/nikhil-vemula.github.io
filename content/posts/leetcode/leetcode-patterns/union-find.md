---
title: 'Union Find'
date: 2024-02-24T13:49:16-05:00
slug: 'union-find'
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
class UnionFind():
    def __init__(self, n):
        self.root = [i for i in range(n)]
        self.sz = [1] * n
        self.n_components = n
    
    def find(self, a):
        root = a
        while root != self.root[root]:
            root = self.root[root]
        
        while a != root:
            nxt = self.root[a]
            self.root[a] = root
            a = nxt
        
        return root
    
    def union(self, a, b):
        root1 = self.find(a)
        root2 = self.find(b)
        if root1 == root2:
            return root1
        
        if self.sz[root1] > self.sz[root2]:
            self.root[root2] = root1
            self.sz[root1] += self.sz[root2]
        else:
            self.root[root1] = root2
            self.sz[root2] += self.sz[root1]
        
        self.n_components -= 1
```

### Problems

#### 2709. Greatest Common Divisor Traversal

- https://leetcode.com/problems/greatest-common-divisor-traversal/description/
- if gcd(a,b) > 1 there share a prime factor
- For every number create undirected edge between num and its prime factors
- Check number of components is 1

#### 1202. Smallest String With Swaps

- https://leetcode.com/problems/smallest-string-with-swaps/description/
- All the indices that are interchangeble form a component
- For each component find string by sorting characted in the indcies of each component

#### 399. Evaluate Division

- https://leetcode.com/problems/evaluate-division/description/
- Custom Union find
