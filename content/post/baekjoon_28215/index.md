---
title: 백준 28215
description: 백준 대피소 풀이
slug: baekjoon_28215
date: 2024-04-12 03:48:00+0000
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
- [이 문제](https://www.acmicpc.net/problem/28215)는 2023년 정보올림피아드 1차 초등부 2번, 고등부 1번으로 출제된 문제 입니다.

## 문제 설명
N개의 집 중 K개의 대피소를 설치하여 대피소 까지의 거리를 최소로 만드는 문제 입니다. 집은 최대 50개, 대피소는 최대 3개로 숫자가 작기 때문에 무작정 다 시도해보는 브루트포스로 풀 수 있습니다.

N=집 수, K=대피소 수
대피소는 집들 중에 있습니다. 

## 풀이 순서 
- 가능한 대피소 조합 만들기
- 집을 for문으로 해서 가장 가까운 대피소 찾아 거리 확정
- 모든 집에서 대피소 거리중 가장 큰 값 저장
- (모든 대피소 조합) 3번 값들 중 가장 작은 값 출력
-  **중요**
    - X, Y는 각각 따로 저장!
    - 최소값을 저장하는 변수에는 float("INF") 로 초기화 
    - 최소, 최대 비교는 if문 보다 min, max 활용!

## 나의 코드
```python
from itertools import combinations #조합
N, K = map(int,input().split()) # n,k(집,대피소) 입력 
x = [0] * N 
y = [0] * N
for i in range(N):
   x[i], y[i] = map(int,input().split()) #위치 입력

comb = list(combinations(range(N),K)) #조합으로 
INF  = float("INF")
r=INF # 결과 값을 찾기 위해 결과 무한 설절

for c in comb:
   case = 0 # 경우
   for home in range(N):
       distance = INF #최솟값을 찾기 위해 거리를 무한으로 설정
       for hide in c:
           tmp = abs(x[home]-x[hide])+abs(y[home]-y[hide]) #거리 구하기
           distance = min(tmp, distance) #최소 거리
       case = max(case, distance) #가장 많은 경우
   r = min(r,case) # 최소 케이스
print(r)
```