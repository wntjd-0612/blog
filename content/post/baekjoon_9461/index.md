---
title: 백준 9461
description: 백준 파도반 수열 풀이
slug: baekjoon_9461



date: 2024-04-12 06:48:00+0000
image: thumb.png
categories:
    - baekjoon
tags:
    - baekjoon
    - ana
    - python
weight: 1

---
# 대피소
- [문제](https://www.acmicpc.net/problem/9461)

## 문제 설명
- 이 문제는 기본적인 [dp](https://namu.wiki/w/%EB%8F%99%EC%A0%81%20%EA%B3%84%ED%9A%8D%EB%B2%95)[^1] 문제이다. 
- 다른 DP와 같이 규칙을 찾아서 그 규칙에 맞게 구현하면 된다.


## 풀이 순서 
- dp 점화식을 구한다
- 구현한다
  -이 문제에는 두가지 점화식이 있다

## 풀이 1
- 이 문제의 수열 (1,1,1,2,2,3,4,5,7,9, ....)을 보면 규칙을 찾을 수 있다.
- i번째 수는 i-1번째수와 i-5번째 수를 더한 값이라는 것이다.(점화식으로 표현하면 dp[i]=dp[i-5]+dp[i-1])
- 이에 따른 코드를 적어보면

```python
def f(n):
    dp = [1,1,1,2,2] #i-5번째 수까지 필요하므로 5개의 배열을 생성한다
    if n<5:return dp[n-1] #만약 i가 5이하이면 인덱싱에 맞춰서 해당 값을 반환해준다
    for i in range(5,n): #i가 5이상이면 for문을 통해 점화식을 써서 값을 구해준다
        dp.append(dp[i-1]+dp[i-5])
    return dp[n-1] #인덱스를 이용하여 해당번째 값을 반환한다

for i in range(int(input())):
    print(f(int(input())))#미친 숏코딩인데 이해하실 수 있죠....?  
```

## 풀이 2
- 이 문제의 수열 (1,1,1,2,2,3,4,5,7,9, ....)을 보면 규칙을 찾을 수 있다.
- i번째 수는 i-2번째수와 i-3번째 수를 더한 값이라는 것이다.(점화식으로 표현하면 dp[i]=dp[i-5]+dp[i-1])
- 이에 따른 코드를 적어보면

```python
def f(n):
    dp = [1,1,1] #i-3번째 수까지 필요하므로 3개의 배열을 생성한다
    if n<3:return dp[n-1] #만약 i가 5이하이면 인덱싱에 맞춰서 해당 값을 반환해준다
    for i in range(3,n): #i가 5이상이면 for문을 통해 점화식을 써서 값을 구해준다
        dp.append(dp[i-2]+dp[i-3])
    return dp[n-1] #인덱스를 이용하여 해당번째 값을 반환한다

for i in range(int(input())):
    print(f(int(input())))#미친 숏코딩인데 이해하실 수 있죠....?  
```
[^2]


[^1]: 나중에 설명하는 글을 쓸껀데 지금은 없으니깐 나무위키 문서 넣어야징
[^2]: 사실상 점화식만 바꾸면 되는게 학계의 점심 뭐먹지?