---
title: 백준 1005
description: 백준 ACM Craft 풀이
slug: baekjoon_1005



date: 2024-04-16 06:48:00+0000
image: thumb.png
categories:
    - baekjoon
    - ana
    - python
tags:
    - baekjoon
    - ana
    - python
weight: 1

---
# ACM Craft
- [문제](https://www.acmicpc.net/problem/1005)

## 문제 설명
문제에 나와있는 그림으로 되어 있을때 4를 건설하기 위해서는 1->2->4,1->3->4순서중 하나로 건설되어야 한다. 이런 선수 관계를 나타내기 위해 `위상 정렬 알고리즘`을 사용해야 한다

그리고, 1->2->4의 경로는 건설시간이 21초 걸리고 1->3->4 경로는 건설시간이 총 120초가 걸리는데 4를 건설하기 위해서는 2와 3이 모두 완료되어야 하기 때문에 2가 빨리 끝나더라도 3을 기다려야 한다.
그래서 4를 건설하기 위한 시간은 1->3->4의 소요시간인 120초인 것이다.

## 풀이 순서 
이제 우리는 경로를 만들고 그 경로에 들어오는것이 두개 이상이라면 그 경로 중 최댓값을 저장하는 방식으로 하면 됩니당.
이 부분을 저장하기 위해서는 dp를 이용해서 두 경로중 최댓값을 저장하는 방식으로 갈 것입니다.
그러면 이 문제에 핵심은 위상정렬을 사용하되, 위상정렬을 하는 과정에서 DP를 이용해 최댓값을 저장해 나간다는 점이다.


## 풀이

```python
import sys
from collections import deque

input = sys.stdin.readline
T = int(input()) #테스트 케이스 입력
for _ in range(T): 
    N, K = map(int, input().split()) #건물개수와 건설 규칙 개수 입력
    time = [0] + list(map(int, input().split())) #각 건물 건설의 걸리는 시간
    seq = [[] for _ in range(N + 1)]
    d = [0 for _ in range(N + 1)]
    dp = [0 for _ in range(N + 1)]

    for _ in range(K):
        a, b = map(int, input().split()) #건설 규칙(순서 입력)
        seq[a].append(b) #그래프화
        d[b] += 1걸리는 시간

    q = deque()
    for i in range(1, N + 1):
        if d[i] == 0:
            q.append(i)
            dp[i] = time[i]

    while q:
        a = q.popleft()
        for i in seq[a]:
            d[i] -= 1
            dp[i] = max(dp[a] + time[i], dp[i])
            if d[i] == 0:
                q.append(i)

    ans = int(input())
    print(dp[ans])
```



[^1]: 나중에 설명하는 글을 쓸껀데 지금은 없으니깐 나무위키 문서 넣어야징
[^2]: 사실상 점화식만 바꾸면 되는게 학계의 점심 뭐먹지?