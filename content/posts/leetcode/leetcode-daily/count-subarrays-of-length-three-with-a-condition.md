---
title: 'Count Subarrays of Length Three With a Condition'
date: 2025-04-26T17:32:04-07:00
slug: 'count-subarrays-of-length-three-with-a-condition'
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

- Return number of length 3 sub arrays whose nums[1]/2 == nums[0] + nums[2]

### Brute force

- We can generate all sub arrays of length 3 O(n^2).

## Match

- Subarray ending at index i trick
- For subarray of length 3 ending at index i we can check if condition passes in constant time.

## Plan

- check nums[0] + nums[1] == nums[2]/2 and res += 1

## Implement

```python
def countSubarrays(self, nums: List[int]) -> int:
    res = 0
    for i in range(2, len(nums)):
        res += (1 if nums[i] + nums[i-2] == nums[i-1]/2 else 0)
    return res
```

## Review

## Evaluate

- Time complexity: `O(n)`