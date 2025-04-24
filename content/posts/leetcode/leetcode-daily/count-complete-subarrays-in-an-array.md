---
title: '2799. Count Complete Subarrays in an Array'
date: 2025-04-23T20:12:39-07:00
slug: 'count-complete-subarrays-in-an-array'
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
- [U]nderstand the problem, ask qeustions and come up with corner test cases.
- [M]atch the leetcode pattern
- [P]lan to using pattern template and data structures
- [I]mplement the code
- [R]eview by running the example and corner test cases
- [E]valuate time and space complexity
```

## Understand

- Need to count the sub arrays the have same number of distinct elements as the array
- For `[1,3,1,2,2]`
    - Subarrays starting with index 0 and 3 distinct elements `[1, 3, 1, 2]` ad `[1, 3, 1, 2, 2]`
    - Subarrays starting with index 1 and 3 distinct elements `[3, 1, 2]` ad `[3, 1, 2, 2]`
    - Total 4

### Brute force

- Generate all sub arrays and also maintain distinct count
- Time complexity `O(n^2)` it passes for given constraints

```python3
def countCompleteSubarrays(self, nums: List[int]) -> int:
        arr_distinct = len(set(nums))
        res = 0
        for i in range(len(nums)):
            sub = set()
            for j in range(i, len(nums)):
                sub.add(nums[j])
                if len(sub) == arr_distinct:
                    res += 1
        return res
```

## Match

- Most subarrays problem can be solved with [sliding window](/posts/leetcode/leetcode-patterns/sliding-window)
- If the current number of distinct elements are less then required, grow (increase right)
- If the number of disctict elements are equal, then all the elements after the right (n - right) are complete sub arrays. Add them to count and shrink (increase left)

## Plan

- We can use hash map to keep track of frequency of each number

## Implement

```python3
def countCompleteSubarrays(self, nums: List[int]) -> int:
    res = 0
    distinct = len(set(nums))
    left = 0
    freq = {}
    for right in range(len(nums)):
        freq[nums[right]] = freq.get(nums[right], 0) + 1
        while len(freq) == distinct:
            res += (len(nums) - right)
            freq[nums[left]] -= 1
            if freq[nums[left]] == 0:
                del freq[nums[left]]
            left += 1
    return res
```

## Review

## Evaluate

- Time complexity: `O(n)`
- Space complexity: `O(n)`


