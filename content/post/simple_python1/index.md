---
title: python 기초문법1
description: python 기초문법-자료형
slug: simple_python1
date: 2024-04-11 06:04:00+0000
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
# python의 자료형
- 파이썬은 자동으로 자료형을 추론해 주지만, 프로그램을 만들때 어떤 자료를 저장할 것인지 알고 있는 것은 매우 중요합니다.
- 파이썬의 자료형은 크게 데이터형과 컨테이너형으로 구분할 수 있습니다. 오늘은 데이터형만 다룰 것입니다.

# 데이터형

## 숫자형
| 항목    | 파이썬 활용 예시               |
|-------|-------------------------|
| 정수    | 123, -456, 0            |
| 실수    | 123.45, -1234.5, 3.4e10 |
| 8진수   | 0o34, 0o25              |
| 16진수  | 0x2A, 0xFF              |

### 정수형
정수형(integer)이란 말 그대로 정수를 뜻하는 자료형을 말한다. 다음은 양의 정수와 음의 정수, 숫자 0을 변수 a에 대입하는 예입니다.
```python
a = 123
a = -178
a = 0
```

### 실수형
파이썬에서 실수형(floating-point)은 소수점이 포함된 숫자를 말한다. 다음은 실수를 변수 a에 대입하는 예이다. 일반적으로 볼 수 있는 실수형의 소수점 표현 방식입니다.
```python
a = 1.2
a = -3.45
```
다음은 ‘컴퓨터식 지수 표현 방식’으로, 파이썬에서는 4.24e10 또는 4.24E10처럼 표현합니다(e와 E 둘 중 어느 것을 사용해도 됩니다).
```python
a = 4.24E10
a = 4.24e-10
```

### 8진수와 16진수

8진수(octal)를 만들기 위해서는 숫자가 0o 또는 0O(숫자 0 + 알파벳 소문자 o 또는 대문자 O)으로 시작하면 됩니다.
```python
a=0o177
print(a)
#127
```

16진수(hexadecimal)를 만들기 위해서는 0x로 시작하면 됩니다.
```python
a=0x8ff
b=0xABC
print(b)
#2748
```
8진수나 16진수는 파이썬에서 잘 사용하지 않는 형태의 숫자 자료형이므로 간단히 눈으로만 익히고 넘어갑시다.


## boll형
- 참과 거짓을 나타내는 자료형, 프로그램의 실행 흐름을 제어 할때 사용
- True(참),False(거짓)의 두 가지 값만 가질 수 있으며, 첫번째는 항상 대문자 
- 자료형의 참과 거짓

| 자료형  | 값       | 참/거짓  |
|------|---------|-------|
| 숫자형  | 0이 아닌수  | True  |
| 숫자형  | 0       | False |
| 문자열  | 'hello' | True  |
| 문자열  | ''      | False |
| 리스트  | [1,2,3] | True  |
| 리스트  | []      | False |
| 튜플   | ()      | False |
| 딕셔너리 | {}      | False |

## 문자열 자료형
- 문자열(string)이란 연속된 문자들의 나열
- 따옴표(큰따옴표, 작은 따옴표) 1개 혹은 3개로 감싸져서 표현된 문자와 단어의 묶음
- 자세한건 입출력문에서 다룰 예정입니다.
