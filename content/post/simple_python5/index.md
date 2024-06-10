---
title: python 기초문법5
description: python 기초문법-조건문
slug: simple_python5
date: 2024-06-02 00:08:00+0000
image: thumb.png
categories:
    - python
tags:
    - basic
    - ana
    - python
weight: 1

---
# 조건문 
- 조건에 따라 서로 다른 명령을 수행할때 사용하는 제어문이다.
- if는 `만약`으로 해석되어 if뒤애 <조선식1>이 참이면 종속된 문장을 실행한다.
- elif는 `아니면 만약`으로 해석하여 if뒤에 <조건식1>이 거짓이고 elif 뒤 <조건식2>가 참이면 종속된 문자를 수행한다
- else는 `아니면`으로 해석하여 if와 elif 뒤에    <조건식>이 모두 거짓일때만 종속된 문장을 수행한다.
- 조건식에는 산술, 비교, 논리 연산자를 사용할 수 있다.

```python
if <조건식 1>:
  <수행할 문장 1>
  <수행할 문장 2>
  ...
elif <조건식2>:
  <수행할 문장1>
  ...
else :
  <수행할 문장1>
  ...

```

- in 키워드는 요소가 리스트, 튜플, 문자열에 있는지에 따라 True 혹릉 False 값을 반환한다.


| in | not in               |
|-----------|------------------|
| X in 리스트        | X not in 리스트           |
| X in 튜플         | X not in 튜플  | 
| X in 문자열| X not in 문자열      |

- 조건문의 참, 거짓에 따라 아무런 일도 수행한니 않도록 설정하려면 pass키워드를 사용한다.
- 조건애 따라 동작하는 반복문을 강제로 빠져나오고 싶을 때는 break 키워드를 사용합니다.