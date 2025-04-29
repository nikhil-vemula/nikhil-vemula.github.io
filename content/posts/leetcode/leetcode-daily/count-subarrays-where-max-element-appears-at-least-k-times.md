---
title: '2962. Count Subarrays Where Max Element Appears at Least K Times'
date: 2025-04-28T19:10:28-07:00
slug: 'count-subarrays-where-max-element-appears-at-least-k-times'
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

- return number of sub arrays that max element atleast k times

### Brute force

- Generate all sub arrays, count mx element. `O(n^2)`

## Match

- Sliding window
- Grow till max_cnt equals k

## Plan

- Grow till max_cnt equals k say i
- Once k then all the sub arrays that end with i+1, i+2 .. len(nums) are also valid sub arrays. res += (len(nums) - right)
- Shrink till max_cnt is less k. During shrink every sub array starting at left if max_cnt satisfied. res += (len(nums) - right)

## Implement

```python
res = 0
mx = max(nums)
left = 0
freq = 0
for right in range(len(nums)):
    freq += (1 if nums[right] == mx else 0)
    if freq == k:
        res += (len(nums) - right)
    while freq == k:
        freq -= (1 if nums[left] == mx else 0)
        left += 1
        if freq == k:
            res += (len(nums) - right)
return res

res = 0
mx = max(nums)
left = 0
freq = 0
for right in range(len(nums)):
    freq += (1 if nums[right] == mx else 0)
    while freq == k:
        res += (len(nums) - right)
        freq -= (1 if nums[left] == mx else 0)
        left += 1
return res
```

## Review

## Evaluate

- Time complexity: `O(n)`