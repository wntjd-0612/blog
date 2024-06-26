---
title: python 기초문법2
description: python 기초문법-자료형
slug: simple_python2
date: 2024-04-12 00:48:00+0000
image: thumb.png
categories:
    - python
tags:
    - basic
    - ana
    - python
weight: 1

---
# python의 자료형
- 파이썬은 자동으로 자료형을 추론해 주지만, 프로그램을 만들때 어떤 자료를 저장할 것인지 알고 있는 것은 매우 중요합니다.
- 파이썬의 자료형은 크게 데이터형과 컨테이너형으로 구분할 수 있습니다. 오늘은 컨테이너형만 다룰 것입니다.


# 컨테이너형
- 여러 개의 변수를 하나의 이름으로 묶어서 관리할 수 있는 데이터 포맷 형태
## 리스트 자료형
- 데이터를 연속적인 공간에 저장하는 자료구조, 서로 다른 자료형도 저장할 수 있습니다.
- 리스트에 각 요소는 쉼표로 구분, 대괄호(`[]`)로 감싸서 표현합니다
### 리스트 연산
- 덧셈기호(`+`)를 사용하여 리스트 연결 연산을 수행할 수 있다.
- 곱셈기호(`*`)를 사용하여 리스트를 반복하는 연산을 수행할 수 있다.
  - 리스트*정수, 정수*리스트 형태로 사용할 수 있다.
- len함수(`len()`)를 사용하여 리스트에 길이를 구할 수 있다.

### 리스트 인덱싱과 슬라이싱


#### 리스트 인덱싱
- 인덱싱(indexing): 수많은 데이터중 원하는 항목을 쉽게 찾도록 '가리키는 것'
- ⭐인덱스 번호는 0부터 시작
- 뒤에서부터 읽기 위해서 마이너스 기호를 사용, 이때 뒤에서부터 첫 번째값은 인덱스`-1`로 표현한다.


#### 리스트 슬라이싱
- 슬라이싱(slicing): 인덱스를 사용하여 수많은 데이터 중 원하는 항목을 `잘라내는 것`
```py
변수명[시작 인덱스 번호:끝 인덱스 번호]
```
- 시작 인덱스 번호에 해당하는 값부터 잘라내며, 끝 인덱스 번호는 포함하지 않음
- 시작 인덱스 번호 생략: 리스트에 시작 ~ 끝 인덱스 번호 전
- 끝 인덱스 번호 생략: 시작 인덱스 번호 ~ 리스트의 끝
- 시작과 끝의 인덱스 번호를 모두 생략: 리스트의 시작 ~ 리스트의 끝

#### 리스트 수정하기
- 문자열은 immutable 타입이기 때문에 인덱싱으로 값을 수정할 수 없지만, 리스트는 인덱싱과 슬라이싱을 사용하여 수정 할 수 있다.
- 리스트의 기존 요소를 빈칸으로 수정함으로써 요소를 삭제할 수 있으며, dle 키워드를 사용하여 삭제할 수 있다.


### 리스트 함수
- 문자열과 마찬가지로 리스트 변수 이름 뒤에 `.`을 붙여 함수를 호출하는 방식으로 사용한다.
- 함수의 종류

|   종류   |     함수    |                       설명                       |
|:------:|:-----------:|:------------------------------------------------:|
| 요소 추가  |  append(x)  |            리스트 맨 뒤에 요소 x 추가            |
|        | insert(x,y) |             인덱스 x 위치에 y를 추가             |
|        |  extend(x)  |          리스트 맨 뒤에 리스트 x를 추가          |
| 요소 삭제  |  remove(x)  | 가장 처음 나오는 x를 찾아 삭제, 없으면 오류 발생 |
|        |    pop()    |         리스트 마지막 요소를 반환 후 삭제        |
| 요소 배열  |    sort()   |                리스트 요소를 정렬                |
|        |  reverse()  |             리스트를 역순으로 뒤집기             |
| 리스트 정보 |   index(x)  |    x를 찾아 인덱스 값을 반환, 없다면 오류 발생   |
|        |   count(x)  |              리스트 내 x의 개수 반환             |

- 빈 리스트에 값을 초기화하지 않은 상태에서는 인덱스를 사용하여 요소에 접근할 수 없다.
- 빈 리스트에 새로운 요소를 추가하기 위해서는 append 함수를 사용해야 하며, 여러 개의 요소를 한 번에 추가하려는 경우 extend 함수를 사용할 수 있다.



## 튜플 자료형
- 몇가지의 다른 점을 제외하면 리스트와 거의 비슷한 자료형이다.
- 아래 몇가지 차이점이 있다
  - 리스트는 [], 튜플은 ()으로 둘러싼다.
  - 리스트는 요솟값의 생성, 삭제, 수정이 가능하지만, 튜플은 요솟값을 바꿀 수 없다.


### 튜플 연산 [^1]
- 덧셈기호(`+`)를 사용하여 튜플 연결 연산을 수행할 수 있다.
- 곱셈기호(`*`)를 사용하여 튜플을 반복하는 연산을 수행할 수 있다.
  - 리스트*튜플, 정수*튜플 형태로 사용할 수 있다.
- len함수(`len()`)를 사용하여 리스트에 길이를 구할 수 있다.

### 튜플 인덱싱과 슬라이싱 [^1]
- 문자열과 리스트의 인덱싱, 슬라이싱과 동일하게 사용할 수 있다.


## 딕셔너리 자료형
- KEY와 VALUE를 한쌍으로 가지며 대응관계를 나타내는 자료형이다.
- 요소값에 대한 순서가 없으며 `"Key: Value"`의 형태로 값을 저장하요 Ket를 통해 Value를 얻을 수 있다.
- 쌍을 이루는 각 요소는 쉼표로 구분하며 중괄호(`{}`)로 감싸서 표현한다.
```python
dic = {key1:value1,key2:value2}
dic = dict(key1=value1,key2=value2)
dic = {} #비어있는 딕셔너리
```
- -주의 사항 -
  - 딕셔너리의 Key에 리스트를 사용할 수 없다.
  - value에는 어떤 값이든 사용할 수 있다.
  - Key는 Value를 찾기 위한 유일한 값이므로 중복을 사용할 경우 하나를 제외한 나머지 요소는 무시된다.



### 요소추가, 수정, 삭제

```python
딕셔너리 이름[key] = value #딕셔너리에 값 추가
del 딕셔너리 이름[key] #{key:value} 쌍 삭제
```

### 딕셔너리 함수

| 함수       | 설명                                       |
|----------|------------------------------------------|
| keys     | key만 모아서 dict_keys 객채 형태로 리턴             |
| values   | value만 모아서 dict_values 객채 형태로 리턴         |
| item     | key,value 쌍을 튜플로 묶어 dict_items 객채 형태로 리턴 |
| clear    | key:value 쌍 모두 지우기                       |
| get(key) | key로 value 얻기                            |
| key in x | key가 딕셔너리 x안에 있는지 조사하여 True/False 반환     |


[^1]:그냥 리스트랑 똑같다



## 집합 자료형
- 집합의 특징을 그대로 구현하여 집합에 관련된 것을 쉽게 처리하기 위한 자료형
- 집합의 각 요소는 쉼표로 구현하고 `{}`로 감싸서 표현한다.
- 요소의 순서가 없고 그로인해 인덱싱과 슬라이싱을 사용할 수 없다.
- 중복되는 값은 한 개만 저장하기 때문에 리스트 혹은 집합은 집합의 원소가 될 수 없다.

```python
집합 이름 = {요소1,요소2, ...}
집합 이름 = set(묶음 자료형)#문자열,리스트, 튜플을 집합으로 변경
집합 이름 = set()
```
### 집합 연산과 함수
- 종류

| 연산  | 설명                                          | 사용 구문             |
|-----|---------------------------------------------|-------------------|
| 교집합 | 집합에 공통으로 들어 있는 원소의 집합                       | & ,intersection() |
| 합집합 | 적어도 한 집합에 들어 있는 원소의 집합                      | \| ,union()       |
| 차집합 | A에 대한 B의 차집합(A-B)은 A의 속하고 B에는 속하지 않는 원소의 집합 | - ,difference()   |


| 함수             | 설명                  |
|----------------|---------------------|
| add(x)         | x 값 추가              |
| update(묶음 자료형) | 묶음 자료형 내 여러개의 요소 추가 |
| remove(x)      | x의 값 삭제             |
