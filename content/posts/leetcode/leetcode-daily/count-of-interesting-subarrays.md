---
title: '2845. Count of Interesting Subarrays'
date: 2025-04-24T20:31:06-07:00
slug: 'count-of-interesting-subarrays'
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

- Need to count subarrays where cnt is number of element such that nums[i] % modulo == k and cnt % modulo == k

### Brute force

- Generate all sub arrays, calculate cnt and  verify cnt % modulo == k.
- Time complexity `O(n^2)` fails for constraint n = 10^5

## Match

### Sliding window
- I thought we can break it smaller problem count subarrays whose cnt = x and apply sliding window for each x value. where x is i  * modulo + k for i in 0, 1, 2, .. and x < len(nums)
- Sliding window will not work as there is no clear condition when to shrink the window.

> Subarray ending at index i trick

### Prefix sum

- We can use [prefix sum](/posts/leetcode/leetcode-patterns/prefix-sum)
- This is similar to Subarray sum equals k with modulo twist.



## Plan

- In subarray sum equals k, prefix[r] - prefix[left] = k which translates to prefix[r] - k = prefix[left]

```python
res = 0
prefix = defaultdict(int)
prefix[0] = 1
s = 0
for n in nums:
    s += n
    res += prefix[s - k]
    prefix[s] += 1
return res
```

- Similarly, (prefix[right] - prefix[left]) % modulo = k translated to (prefix[right] - k + modulo) mod modulo =  prefix[left] mod modulo
```
(prefix[right] - prefix[left]) mod modulo = k
=> prefix[right] - prefix[left] = k + c * modulo
=> prefix[right] - k = prefix[left] + c * modulo 
=> (prefix[right] - k) mod modulo = (prefix[left] + c * modulo) mod modulo  -- using modulo both side
=> (prefix[right] - k) mod modulo =  prefix[left] mod modulo  -- using (a + c.m) mod m = a mod m
=> (prefix[right] - k + modulo) mod modulo =  prefix[left] mod modulo -- using  a mod m = (a + c.m) mod m
```

```python
res = 0
prefix = defaultdict(int)
prefix[0] = 1
c = 0
for n in nums:
    c += ((n % modulo = k) if 1 else 0)
    res += prefix[c - k + modulo]
    prefix[c % modulo] += 1
return res
```

## Implement

```python
res = 0
prefix = defaultdict(int)
prefix[0] = 1
c = 0
for n in nums:
    c += ((n % modulo = k) if 1 else 0)
    res += prefix[c - k + modulo]
    prefix[c % modulo] += 1
return res
```

## Review

## Evaluate

- Time complexity: `O(n)`

