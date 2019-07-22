---
layout: post
title: "REST-API 설계하기"
description: "더욱 명확한 REST-API 설계 방안"
date: 2019-07-19
categories: [HTTP]
tags: [Backend, http, https, rest, network]
comments: true
share: true
---

## REST
* `Representational State Transfer`의 약자로 월드 와이드 웹(www)의 기술과 HTTP프로토콜을 그대로 활용하여 웹의 장점을 최대한 활용할 수 있는 아키텍처 기술이다.
* HTTP URI`(Uniform Resource Identifier)`를 통해 자원을 명시하고, HTTP 메소드를 통해 해당 자원을 CRUD하는것을 의미한다.
* 공식적으로 표준화된 표준규약이 없다.

## REST API
* 위 설명한 `REST`기반으로 서비스의 API를 제공하는 것.

## REST API 설계 규칙
1. URI만으로 어떤 정보를 제공할 것인지 명확해야 한다.
    - 동사를 사용하지 않는다. 명사를 사용하며 이 때에도 **단수명사**를 사용한다.
    - ex) GET : /user/1 (ok)
    - ex) GET : /users/1 (err)
2. HTTP행위에 맞게 사용한다.

    |약어|C|R|U|D|
    |:---:|:---:|:---:|:---:|:---:|
    |-|Create|Read|Update|Delete|
    |의미|생성|조회|수정|삭제|
    |HTTP|post|get|put|delete|
3. URI에 HTTP Method가 들어가지 않는다.
    - ex) GET : /user/1 (ok)
    - ex) GET : /user/get/1 (err)
4. 최대한 사용을 자제해야하지만 불가피하게 단어가 길어질 경우 - 하이픈을 사용한다.
5. HTTP response CODE는 HTTP문서를 따른다.
    - [HTTP 상태코드 확인](https://ko.wikipedia.org/wiki/HTTP_%EC%83%81%ED%83%9C_%EC%BD%94%EB%93%9C)

## RESTful
* REST에서 설명하였듯이 공식적으로 표준화된 규약이 없다.
* `REST API`를 제공하는 서비스를 RESTful하다고 부른다. (필자마다 개념이 조금씩 다를 수 있다.)
* 이해하기 쉬운 REST API를 설계하는것에 목적이 있다.
* RESTful한 API는 성능향상의 목적이 아니기 때문에 최대한 일관성있고 명확하게 설계해야한다.
      


---
* References  
1. https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html
2. https://bcho.tistory.com/954