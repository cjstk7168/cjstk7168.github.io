---
path: "/6"
layout: post
title: "[Vue.js Express] 이용한 개발환경 세팅하기"
description: "Vue.js와 Express 연동하기"
date: 2019-06-01
categories: [Infra]
tags: [서버, Backend, Infra, Express, Vue.js]
comments: true
share: true
---

#### Express와 Vue.js를 이용한 개발환경 세팅하기
구글에 검색해보면 위 키워드로 검색하면 무수히 많은 자료가 나온다.
여러 자료를 보고 내 입맛에 딱 맞는 설명을 찾기 어려워 (좀 더 검색하면 있을지도?)
정리도 할 겸 남겨보도록 한다.

---
#### 개념도
![image](/images/post_4/img_structure.png)

IE, Chrome등의 브라우저를 통해 Vue.js로 만들어진 웹페이지에 접속하고 Express로 만들어진 서버와 통신한다.
Express는 MySQL, ORACLE등의 데이터베이스와 연결된 형태를 가지고 있다.

---

### Backend 설정
```console
npm install express-generator -g
express --ejs backend #express-generator를 이용해 express 프로젝트를 생성한다
cd backend
npm install
npm start # 서버 가동
```

위와 같은 순서로 간단하게 Express프레임워크의 Backend구성이 끝났다.

### FrontEnd 설정
```console
npm install -g vue-cli
vue init webpack frontend # frontend 폴더에 vue프로젝트를 생성한다
# 여러가지 설정하는것이 나오는데 vue-router, eslint 등 필요한것을 Y로 설정.
cd front
npm install
``` 

_vue init webpack fronted 실행 시 물어보는 질문_
```console
? Project name :
? Project description A Vue.js : 
? Author : 
? Vue build standalone :
? Install vue-router? :
? Use ESLint to lint your code? :
? Pick an ESLint preset Standard :
? Set up unit tests : 
? Pick a test runner :
? Setup e2e tests with Nightwatch? :
? Should we run `npm install` for you after the project has been created? (recommended) :
```


위와 같은 순서로 이번에도 간단하게 Vue.js프레임워크의 Frontend구성이 끝났다.

---

### ProxyTable 설정
여기까지 따라왔다면 현재 Backend, Frontend의 2개의 폴더가 생겼을 것이다.  
project  
-- frontend    
└ backend
        
현재 2개의 폴더는 각각 따로 실행되고 있다.  
port : (frontend : 8080, backend: 3000)  
이 2개를 연결해줘야 한다.

/frontend/config/index.js 를 열어 편집
```console
proxyTable: {
    '/api': {
        target: 'http://localhost:3000/api'
    }
}
```
위와같이 설정해주면 frontend에서 :8080/api/.. 와같이 시작하는 url은  
backend의 :3000/api/.. 로 proxy해준다.

이제 2개의 프로젝트가 정상적으로 연결되었다.

터미널 2개를 띄워 각각 프로젝트를 실행해준다.  
```console
frontend - npm start - http://localhost:8080  
backend - npm start - http://localhost:3000
```

http://localhost:8080 에서 http://localhost:8080/api/..를 실행해보면  
http://localhost:3000/api/.. 에서 반응이 오는것을 볼 수 있다.


너무나 간단한 기본 개발환경 세팅방법.  
_참 쉽죠?_