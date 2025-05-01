---
title: '2071. Maximum Number of Tasks You Can Assign'
date: 2025-04-30T21:31:33-07:00
slug: 'maximum-number-of-tasks-you-can-assign'
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

- Return max number of tasks that can be completed using the the given wokers and pills.

### Brute force

- Brute is searching searching all possiblities
- Check if k number of tasks can be completed and iterate k from 0 to len(tasks)
- Check logic would be greedy logic either you get it or not. I did not.
    - Select k tasks with minimum effort
    - Select k workers with maximum strength
    - Select a task with highest effort
        - If strongest worker can do it. Good.
        - If not give pill to the weakest worker you can do it.
        - If both not possible. Task can not be completed.

## Match

- Binary search can be used for problems where we search for something that looks like `[Possible, Possible, Possible, Not possbile, Not possbile, Not possible]

## Plan

- use binary search for k

## Implement

```python
tasks.sort()
workers.sort()

def check(mid):
    p =  pills
    selected_tasks = tasks[:mid]
    selected_workers = workers[len(workers)-mid:]

    for t in selected_tasks[::-1]:
        if not selected_workers:
            return False
        if t <= selected_workers[-1]:
            selected_workers.pop()
        else:
            if p == 0:
                return False
            idx = bisect.bisect_left(selected_workers, t - strength)
            if idx == len(selected_workers):
                return False
            p -= 1
            selected_workers.pop(idx)
    return True

left = 0
right = min(len(tasks), len(workers))
while left <= right:
    mid = (left + right) // 2
    if check(mid):
        left = mid + 1
    else:
        right = mid - 1
return left - 1
```

## Review

## Evaluate

- Time complexity: `nlog(n) + mlog(m) + min(m,n)log^2(min(m, n))`