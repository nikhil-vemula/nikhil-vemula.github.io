---
title: '2444. Count Subarrays With Fixed Bounds'
date: 2025-04-25T22:41:30-07:00
slug: 'count-subarrays-with-fixed-bounds'
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

- Need to count subarrays where min = minK and max = maxK

### Brute force

- Generate all sub arrays, track min and max
- Time complexity `O(n^2)` fails for constraint n = 10^5

## Match

- Sliding window? two constraints mix and max unlike freq of something
- Prefix sum? two things to track unlike sum till i or cnt till i
- [Two pointers](/posts/leetcode/leetcode-patterns/two-pointers/)
    - consider minK=2, maxK=6, arr=[2, 3, 6, 4] sub arrays [2, 3, 6] and [2, 3, 6, 4] if we can track the most recent min position
    - consider minK=2, maxK=6, arr=[6, 3, 2, 4] sub arrays [6, 3, 2] and [6, 3, 2, 4] if we can track the most recent max position
    - consider minK=2, maxK=6, arr=[4, 6, 3, 2, 5] sub arrays [4, 6, 3, 2] , [4, 6, 3, 2, 5] , [6, 3, 2] and [6, 3, 2, 5] if we can track the number of numbers before min_pos that are greater than equal to minK i.e if we can track left position where nums[left] < minK or nums[right] > maxK => position where number does not belong (minK, maxK). we can calculate min_pos - left to get the numbers that are greater or equal to minK

## Plan

- min_pos for most recent position of minK
- max_pos for most recent position of maxK
- left for position where nums[left] < minK or nums[left] > maxK
- min(min_pos, max_pos) ensures min and max are included
    - if mink not found it would be -1 and res += 0 similarly for maxK
    - if left is reset the min(min_pos, max_pos) < left and max(0, this_value) then res += 0

## Implement

```python
res = 0
mi_pos = mx_pos = left = -1
for i in range(len(nums)):
    if nums[i] < minK or nums[i] > maxK:
        left = i
    
    if nums[i] == minK:
        mi_pos = i
    
    if nums[i] == maxK:
        mx_pos = i
    
    res += max(0, min(mi_pos, mx_pos) - left)
return res
```

## Review

## Evaluate

- Time complexity: `O(n)`
