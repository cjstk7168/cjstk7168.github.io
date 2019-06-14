---
layout: post
title: "[Vue.js] Mixins 사용하기"
description: "컴포넌트의 재사용성 끌어올리기"
date: 2019-06-11
categories: [Vue.js]
tags: [FrontEnd, Vue.js]
comments: true
share: true
---

## 믹스인
Mixins는 Vue 컴포넌트에 재사용 가능을 배포하는 유연한 방법입니다. mixin 객체는 모든 구성요소 옵션을 포함할 수 있습니다. 컴포넌트에 mixin을 사용하면 해당 mixin의 모든 옵션이 컴토넌트의 고유 옵션에 "혼합"됩니다.

```javascript
// mixin 객체 생성
var myMixin = {
  created: function () {
    this.hello()
  },
  methods: {
    hello: function () {
      console.log('hello from mixin!')
    }
  }
}

// mixin을 사용할 컴포넌트 정의
var Component = Vue.extend({
  mixins: [myMixin]
})

var component = new Component() // => "hello from mixin!"
```

---
* 참고  
1. https://kr.vuejs.org/v2/guide/mixins.html