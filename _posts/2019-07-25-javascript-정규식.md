---
path: "/16"
layout: post
title: "Javascript 정규 표현식 사용하기"
description: "정규식의 패턴 이해하고 사용하기"
date: 2019-07-25
categories: [JavaScript]
tags: [Backend, JavaScript, String]
comments: true
share: true
---

## 정규 표현식
* 문자열에 나타나는 특정 문자 조합과 대응시키기 위해 사용하는 패턴. 이 패턴들은 `RegExp`의 `exec메소드, `search메소드, `split`메소드와 함께 사용된다.

* 정규 표현식은 줄여서 `정규식`이라고 부른다.

## 정규식 만들기
정규식 만들기에는 두 가지 방법이 있다.
1. 정규식 리터럴(슬러쉬 `/`로 감싸는 방법)을 사용하는 방법
```
const re = /ab+c/;
```
리터럴로 사용하면 스크립트가 불러와질 때 컴파일이 된다. 정규식이 상수로 이루어져 있다면 리터럴 방식이 성능향상에 도움이 된다.

2. `RegExp`객체의 생성자 함수를 호출하는 방법
```
const regexp = new RegExp('ab+c');
```
생성자 함수를 사용하면 함수가 실행될 때 컴파일이 된다. 패턴이 변경되는 경우가 있거나 사용자의 입력을 받아 패턴처리하는 경우에는 생성자 함수를 사용한다.

## 정규식 패턴작성하기
`/abc/` 와 같이 단순히 사용할 수 있지만, 좀 더 복잡한 특수 문자 사용하는 방법에 대해 정리해본다.

| Character | Meaning |
| --- | :--- |
| ` \ ` | 역슬러시 뒤에 오는 문자는 특별함을 의미한다.<br><br>`/a*/` 은 a라는 문자가 0개이상 나타남을 의미하지만, `/a\*` 이라 표현하면 `a*` 문자 그대로를 해석한다.  |
| `^` | 시작 부분에 대응한다. `^A`라 함은 A로 시작하는 문자를 표현한다. |
| `&` | 끝 부분과 대응한다. `^`와 반대이다. |

## 플래그
플래그를 설정해줄 수 있으며 순서에는 구분이 없다.

| Flag | Description |
| --- | :--- |
| `g`| 전역 검색 |
| `i`| 대소문자 구분 없음 |


## 정규식 테스트해볼 수 있는 사이트
[https://regexr.com/](https://regexr.com/)

---
* References  
1. https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D
2. https://code.tutsplus.com/tutorials/8-regular-expressions-you-should-know--net-6149