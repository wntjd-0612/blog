---
title: python 기초문법3
description: python 기초문법-자료형
slug: simple_python3
date: 2024-05-02 00:48:00+0000
image: thumb.png
categories:
    - python
    - ana
tags:
    - basic
    - ana
    - python
weight: 1

---

## python 입출력문
`python()`함수는 마지막 데이터에서 뒤에 줄 바꿈 문자를 포함한디.
```py
print('a')
print('b')
```
이를 무시하기 위해서는 
```py
print('a',end='')
print('b')
```
을 통해서 무시할 수 있다.

- print() 함수에서 여러줄을 출력할 때는 따옴표를 연속으로 3개 사용하여 여러줄에 해당하는 문자영을 한번에 담거나 `\n`을 사용하여 줄바꿈을 해줄 수 있다.

## python 변수 
- 데이터를 저장하는 공간을 의미하며, 변하는 값을 저장할 수 있어서 `변수`라고 한다.
- 변수에 이름을 붙인 것을 변수명이라고 하며 변수 이름으로 한글을 사용할수 있다.
- 파이썬은 변수의 이름을 적어 주는 것만으로 변수를 선언할 수 있으며, 자료형을 명시하지 않아도 저장되는 값에 따라 자료형(데이터 타입)을 자동으로 추론한다.
- 대입 연산자를 통해 변수에 값을 할당할 수 있으며, 이를 초기화라고 한다.

## python 입력변수
`input()`
- input() 함수는 입력받은 값을 문자열로 저장한다.
- 입력받은 값으로 산술 연산을 하기 위해서는 해당 값을 정수형(int)로 혹은 실수(float)으로 변화해야 한다.
```
a=input()
print(type(a))
a=int(input())
print(type(a))
```
