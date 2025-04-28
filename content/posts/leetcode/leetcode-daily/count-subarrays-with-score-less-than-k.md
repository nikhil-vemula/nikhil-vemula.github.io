---
title: '2302. Count Subarrays With Score Less Than K'
date: 2025-04-27T17:53:28-07:00
slug: 'count-subarrays-with-score-less-than-k'
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

```
UMPIRE
- [U]nderstand the problem, ask questions and come up with corner test cases.
- [M]atch the leetcode pattern
- [P]lan to using pattern template and data structures
- [I]mplement the code
- [R]eview by running the example and corner test cases
- [E]valuate time and space complexity
```

## Understand

- Return number of sub arrays whose sum * len < k

### Brute force

- Generate all subarrays. `O(n^2)`

## Match

- Sliding window
- Shrink while s * l >= k, grow otherwise

## Plan

- For every ith idx if sum(nums[:i]) * len(nums[:i]) < k then we increase the result by (right - left + 1).
- Because of the conidition that array contains only positive integers, we can be sure that all elements that start at left, left+1, left+2 .. right are valid subarrays.


## Implement

```python
res = 0
left = 0
s = 0
for right in range(len(nums)):
    s += nums[right]
    while left < right and s * (right - left + 1) >= k:
        s -= nums[left]
        left += 1
    if s * (right - left + 1) < k:
        res += (right - left + 1)
return res
```

## Review

## Evaluate

- Time complexity: `O(n)`