---
path: "/4"
layout: post
title: "Dont't use Array.forEach()"
description: "Node.js에서 for문 성능향상 팁"
date: 2019-05-28
categories: [JavaScript]
tags: [서버, Backend, Node, Javascript]
comments: true
share: true
---


### Node.js에서 forEach를 사용하지 마십시오.  
사소하지만 작은 습관이 성능을 더 빨라지게 합니다.

---

JavaScript에서 Array.forEach는 for()문법에 비해 95% 더 느립니다.  
**Dont't use :**
```javascript
Array.forEach( item => {
    func(item);
})
```
**Use :**
```javascript
for(let i = 0, len = Array.length; i < len; i++){   
    func(arr[i]);
}
```

**Also :** 
```javascript
for(let i = 0; i < Array.length; i++){   
    func(arr[i]);
}
```
위와 같은 코드는 for문을 한 바퀴 돌 때마다 Array.length를 계산하기 때문에 성능이 떨어질 수 있다.

#### 참고사이트
* [원본](https://coderwall.com/p/kvzbpa/don-t-use-array-foreach-use-for-instead)


