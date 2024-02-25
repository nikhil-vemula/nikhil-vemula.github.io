---
title: 'Leetcode Patterns'
weight: 1
date: 2024-02-23T15:39:33-05:00
slug: 'leetcode-patterns'
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
ShowPostNavLinks: false
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

- To find the final value at the end of updated by multiple range queries. We can used [sweep line]({{<ref "sweep-line">}})
- For substring and sub array problems you can use [sliding window]()
- For range queries with out updates we can use [pre-calculation]()

### Tree

- Maximum height for non-root node

### Graph

#### Traversals

1. [BFS]({{<ref "graph-bfs">}})
    - Revisiting the node based on a condition like [this]({{<ref "graph-bfs#2092-find-all-people-with-secret">}})
2. DFS
3. Level order traversal

#### Shortest path

1. [Dikstra's single source]({{<ref "dijkstra">}})
    - Edge weights can not be negative
    - Directly apply algorithm and return the shortest distance from src to destination
    - We can modify the addition operator for some variations like [this]({{<ref "dijkstra#1631-path-with-minimum-effort">}})
2. [Bellman ford]({{< ref "bellman-ford" >}})
    - Edge weights can be negative but should not have negtaive sum cycles.
    - The algorithm works exploring the edges that are `k` edges far from the source node. Therefore, can be used to solve problems which asks for shortest distance within `k` hops

#### Union Find

1. We can aswer if two nodes belongs to same component
2. Number of components

### Misc

- [Sweep line]({{<ref "sweep-line">}})
- Sqrt decomposition
- Range queries