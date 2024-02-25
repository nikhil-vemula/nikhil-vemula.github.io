---
title: 'Math'
date: 2024-02-25T12:33:30-05:00
slug: 'math'
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

- if gcd(a,b) > 1 there share a prime factor

### Sieve of eratosthenes

```python
n = 100

sieve = [0]*(n+1)
for i in range(2, n+1):
    if sieve[i] == 0:
        for j in range(i, n+1, i):
            sieve[j] = i

primes = []
for i in range(2, n+1):
    if sieve[i] == i:
        primes.append(i)

print(primes)
```

### Prime factors

```python
n = 12

sieve = [0]*(n+1)
for i in range(2, n+1):
    if sieve[i] == 0:
        for j in range(i, n+1, i):
            sieve[j] = i
            
pfactors = []
val = n
while val > 1:
    prime = sieve[val]
    pfactors.append(prime)
    while val % prime == 0:
        val //= prime

print(pfactors)
```
