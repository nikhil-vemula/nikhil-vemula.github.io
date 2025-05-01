---
title: '1295.Find Numbers With Even Number of Digits'
date: 2025-04-29T17:52:59-07:00
slug: 'find-numbers-with-even-number-of-digits'
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

- Find count of numbers whose digits are divisible by 2

### Brute force

- For each number find number of digits % 2 == 0 and res += 1

## Match

NA

## Plan

- no_of_digits % 2 == 0, res += 1

## Implement

```python
res = 0
def nDigits(n):
    res = 0
    while n:
        res += 1
        n //= 10
    return res
for n in nums:
    if nDigits(n) % 2 == 0:
        res += 1
return res
```

## Review

## Evaluate

- Time complexity: `O(n)`