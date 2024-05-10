---
title: 'Guide to Leetcoding'
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

## Approach

1. Try to solve the problem using brute force. This helps to come up with a logic required for the problem.
2. Identify the pattern.
3. Implement the solution using the pattern.
4. Identify time and space complexity.

## Tips to match the pattern

1. If the problem involves exploring a search space in a tree or a graph then we can consider [BFS]({{<ref "#bfs">}}) or [DFS]({{<ref "#dfs">}}).
    - If the problem requires minimum number of steps then we should use BFS instead of DFS to explore.

## Patterns

### Prefix

#### Problems

- Subarray sum k
```python
res = 0
presumToCount = defaultdict(int)
presum = 0
for num in nums:
    presum += num
    if presum == k:
        res += 1
    res += presumToCount[presum - k]
    presumToCount[presum] += 1
return res
```

- [1915. Number of Wonderful Substrings](https://leetcode.com/problems/number-of-wonderful-substrings/description/)
- Similar to sub array sum equals k, but we use bitmask and xor operations on the prefix values to find the substrings with zero odd count (prefix is zero) and with 1 odd count.

### Sliding window

#### Problems

- [2962. Count Subarrays Where Max Element Appears at Least K Times](https://leetcode.com/problems/count-subarrays-where-max-element-appears-at-least-k-times/description/)
- [992. Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/description/)
- [2444. Count Subarrays With Fixed Bounds](https://leetcode.com/problems/count-subarrays-with-fixed-bounds/description/)

### Heap

#### Problems

- [786. K-th Smallest Prime Fraction](https://leetcode.com/problems/k-th-smallest-prime-fraction/description/)
    - Merging k sorted lists

### BFS

- Level order traversal is a version of BFS.
- We can revisit a node based on a condition. Ex. `2092. Find All People With Secret`

#### Problems

- [752. Open the Lock](https://leetcode.com/problems/open-the-lock)
    - As we need minimum number of turns we should use BFS (Level order traversal)

- [2092. Find All People With Secret](https://leetcode.com/problems/find-all-people-with-secret)
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

### DFS

- Eulerian path [here]({{<ref "graph-dfs#332-reconstruct-itinerary">}})
- Detecting cycle in directed graph[here]({{<ref "graph-dfs#1059-all-paths-from-source-lead-to-destination">}})

#### Problems

- [834. Sum of Distances in Tree](https://leetcode.com/problems/sum-of-distances-in-tree/description/)
    - Use recursion to find distances from root to all other nodes.
    - Use the root value to calculate the answer for the child.

### Topological sort

#### Problems

#### Course sechdule II

```python
adj = defaultdict(list)
for u, v in prerequisites:
    adj[u].append(v)

visiting = set()
finished = set()
order = []
def dfs(u):
    if u in visiting:
        return False
    
    if u in finished:
        return True
    
    visiting.add(u)
    for v in adj[u]:
        if not dfs(v):
            return False
    visiting.remove(u)
    finished.add(u)
    order.append(u)
    return True

for i in range(numCourses):
    if not dfs(i):
        return []

return order
```

```python
in_degree = [0] * numCourses
adj = defaultdict(list)
for u, v in prerequisites:
    adj[u].append(v)
    in_degree[v] += 1

q = deque()
for i in range(numCourses):
    if in_degree[i] == 0:
        q.append(i)

res = []
while q:
    u = q.popleft()
    res.append(u)
    for v in adj[u]:
        in_degree[v] -= 1
        if in_degree[v] == 0:
            q.append(v)

return [] if len(res) != numCourses else res[::-1]
```

### Dynammic programming

- Longest Increasing Subsequence
    - [2370. Longest Ideal Subsequence](https://leetcode.com/problems/longest-ideal-subsequence/description/) 
    - We need not iterate all the previous indexes.

### Trie

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.endOfWord = False

class Trie:

    def __init__(self):
        self.root = TrieNode()

    def insert(self, word: str) -> None:
        curr = self.root
        for c in word:
            if c not in curr.children:
                curr.children[c] = TrieNode()
            curr = curr.children[c]
        curr.endOfWord = True


    def search(self, word: str) -> bool:
        curr = self.root
        for c in word:
            if c not in curr.children:
                return False
            curr = curr.children[c]
        return curr.endOfWord

    def startsWith(self, prefix: str) -> bool:
        curr = self.root
        for c in prefix:
            if c not in curr.children:
                return False
            curr = curr.children[c]
        return True
```

#### Problems

- [1065. Index Pairs of a String](https://leetcode.com/problems/index-pairs-of-a-string/description/)
- [421. Maximum XOR of Two Numbers in an Array]()


<!-- ## Archive notes

- To find the final values of an array at the end of range updates. We can use the [sweep line]({{<ref "sweep-line">}}) technique.
- For substring and sub array problems you can use [sliding window]()
- For range queries with out updates we can use [pre-calculation]()
- You can use BFS when shortest path is needed.
- When nothing seems to fit smart search using [binary search]({{< ref "binary-search" >}})
- Matrix tricks
    - Diagonal i == j or i + j == n

### Arrays

- Maximum sum subarray
- [Rotated sorted arrays]({{<ref "rotated-sorted-arrays">}})

#### Sliding window

- 525. Contiguous Array


### Linked list

- Slow and fast pointers
- Dummy node

### Two pointers

- Merging two sorted lists. Interesting variation [here]({{<ref "two-pointers#977-squares-of-a-sorted-arrayn">}})

###  Stack

### Divide and conquer

- Merge k sorted lists

### DP

- DP where we only expand probable candidates
- Track the items
- Only store necessary items as parameters. Use return wisely.

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

#### Topological sort

### Trie



### Misc

- [Sweep line]({{<ref "sweep-line">}})
- [Quick select]({{<ref "quick-select">}})
- Sqrt decomposition
- Range queries
- Permuation of string

# Group of problems

- Maxsum subarray
    - [152. Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/description/)
- 153. Find Minimum in Rotated Sorted Array
    - Find target in Rotated sorted array
- Buy Sell Stock
    - Best Time to Buy and Sell Stock
    - Best Time to Buy and Sell Stock II
    - Best Time to Buy and Sell Stock III
    - Best Time to Buy and Sell Stock IV
    - Best Time to Buy and Sell Stock with Cooldown
- 647. Palindromic Substrings
    - 5. Longest Palindromic Substring
- [55. Jump Game](https://leetcode.com/problems/jump-game/description)
- Meeting room
- Merge lists
    - Merge two sorted lists - Two pointer
    - [378. Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/)
    - Merge k sorted lists - Divide and conquer
- Stack - Paranthesis matching
    - [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)
    - [Minimum number of paranthesis to remove to make it valid](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/)
    - [Length of longest valid paranthesis](https://leetcode.com/problems/longest-valid-parentheses/)
    - [678. Valid Parenthesis String](https://leetcode.com/problems/valid-parenthesis-string)
- Backtracking - [Combination Sum]({{< ref "comb-sum">}})
- Subsets
    - Subset sum equals k
    - 416. Partition Equal Subset Sum
        - 698. Partition to K Equal Sum Subsets
- Longest increasing subsequence
    - Number of longest increasing subsequences -->