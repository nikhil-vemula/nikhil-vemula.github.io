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

- To find the final values of an array at the end of range updates. We can use the [sweep line]({{<ref "sweep-line">}}) technique.
- For substring and sub array problems you can use [sliding window]()
- For range queries with out updates we can use [pre-calculation]()
- You can use BFS when shortest path is needed.
- When nothing seems to fit smart search using [binary search]({{< ref "binary-search" >}})

- Matrix tricks
    - Diagonal i == j or i + j == n

### Two pointers

- Merging two sorted lists. Interesting variation [here]({{<ref "two-pointers#977-squares-of-a-sorted-arraynl">}})

###  Stack

### Divide and conquer

- Merge k sorted lists

### DP

- DP where we only expand probable candidates
- Track the items

### Tree

- Return negative value to figure out the location of the target like [this]({{<ref "tree##2385-amount-of-time-for-binary-tree-to-be-infected">}})

### Graph

#### Traversals

1. [BFS]({{<ref "graph-bfs">}})
    - Revisiting the node based on a condition like [this]({{<ref "graph-bfs#2092-find-all-people-with-secret">}})
2. [DFS]({{<ref "graph-dfs">}})
    - Eulerian path [here]({{<ref "graph-dfs#332-reconstruct-itinerary">}})
    - Detecting cycle in directed graph[here]({{<ref "graph-dfs#1059-all-paths-from-source-lead-to-destination">}})
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
- [Quick select]({{<ref "quick-select">}})
- Sqrt decomposition
- Range queries
- Permuation of string

# Group of problems

- Jump game
- Meeting room
- Merge lists
    - Merge two sorted lists - Two pointer
    - Merge k sorted lists - Divide and conquer
- Paranthesis matching
    - Valid paranthesis
    - [Minimum number of paranthesis to remove to make it valid](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/)
    - [Length of longest valid paranthesis](https://leetcode.com/problems/longest-valid-parentheses/)