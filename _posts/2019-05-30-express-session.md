---
layout: post
title: "ExpressSession 사용해보기"
description: ""
date: 2019-05-30
categories: [Infra]
tags: [서버, Backend, Infra, Express]
comments: true
share: true
---

### ExpressSession
ExpressSession은 Express 프레임워크에서 세션관리를 위한 미들웨어입니다.  

### app.js를 편집합니다.
```javascript
const session = require('express-session');

app.use(
  expressSession({
    store: new RedisStore({
      host: {{ host }},
      port: {{ port }},
      prefix: {{ prefixStr }},
    }),
    resave: false,
    saveUninitialized: false,
    secret: '!$#%#$%#$#',
  })
);
```

* store - 세션을 저장할 장소를 지정한다. 위 예제에서는 redis에 저장한다.
- 파일 / redis / database 등 설정 가능
* secret - 쿠키의 임의로 변조하는것을 막기 위하여 설정하는 값. 이 값을 통하여 암호화하여 저장한다.
* resave - 세션을 언제나 저장할지 정하는 값. false권장
* saveUninitialized - 세션이 저장되기 전에 uninitialized상태로 미리 저장한다.
* cookie - 쿠키사용여부와 그에대한 속성설정