---
title: 'Leetcode Patterns'
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

### Misc 
#### Range queries:

#### Tree

- Maximum height for non-root node

### Graph

#### Shortest path

1. Problem can be modeled as graph and we need to find the shortest path between two nodes with constraints
2. [Dikstra's single source]({{<ref "dijkstra">}})
    - Edge weights can not be negative
    - Directly apply algorithm and return the shortest distance from src to destination
    - We can modify the addition operator for some variations like [this]({{<ref "dijkstra#1631-path-with-minimum-effort">}})
3. [Bellman ford]({{< ref "bellman-ford" >}})
    - Edge weights can be negative but should not have negtaive sum cycles.
    - The algorithm works exploring the edges that are `k` edges far from the source node. Therefore, can be used to solve problems which asks for shortest distance within `k` hops