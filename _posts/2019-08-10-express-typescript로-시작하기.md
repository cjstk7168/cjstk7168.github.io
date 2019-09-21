---
layout: post
title: "TypeScript로 Express시작하기"
description: "express를 이용한 api서버 세팅 with TypeScript"
date: 2019-08-10
categories: [Infra]
tags: [Infra, server, api, node, typescript]
comments: true
share: true
---

## TypeScript 설치
우선 `express`를 먼서 설치해준다.
본 예제에서는 서버용 `express`를 세팅하기위하여 프로젝트명을 `api`로 설정한다.
```
$ npm install express-generator -g
$ express api
```
그리고 기본적인 모듈 설치
```
$ cd api
$ npm install
```

이제 기본적인 express세팅은 끝이났다.
다음으로 TypeScript사용을 위한 세팅을 한다.

```
# make package.json
$ npm init -y

# install save devDependencies
$ npm i -D typescript
+ typescript@3.5.3

# install @types
$ npm i -D @types/node @types/express
+ @types/express@4.0.37
+ @types/node@8.0.30
```

빌드를 위한 TypeScript설정을 한다.

```
# make tsconfig.json
$ npx tsc -init
```

프로젝트를 시작할 때 TypeScript를 빌드 후 Node.js로 실행하는 스크립트를 편집한다.
```
# package.json
{
  "scripts": {
    "start": "tsc && node dist"
  }
}
```

여기까지 했으면 TypeScript사용을 위한 express세팅이 완료되었다.  
`npm start`를 통하여 정상적으로 동작하는지 확인해본다.