---
path: "/20"
layout: post
title: "[Github] package registry 이용하기"
description: "[beta] github를 이용한 package배포"
date: 2019-08-21
categories: [Infra]
tags: [Infra, Github]
comments: true
share: true
---

## package registry
2019년 5월 github에서 Package Registry를 공개했다.  
`npmjs`와 마찬가지로 github에서도 npm저장소를 제공한다는 의미이다.

(포스팅을 작성하는 현재는 beta 버전이다). [자세히보기](https://github.com/features/package-registry)

`npm`, `Docker`, `Maven`, `NuGet`, `RubyGems`를 지원한다.

본 포스팅에서는 npm기준으로 작성해보고자 한다.

## github package registry 장점
* 한 저장소에서 비공개/공개 package저장소를 이용할 수 있다.
* 하나의 권한으로 관리할 수 있다. (access token)
* global을 통한 빠른 CDN다운로드 제공
* 다양한 언어를 하나의 깃헙 인증권한을 통해 권한 제어가 가능하다. (이건 좀 편한듯)

깃헙은 이전에 비결제 사용자에게도 프라이빗 환경을 제공한다. package registry역시 무료로 이용가능하다는점이 npmjs와 가장 큰 차이일것같다.

또한 깃헙에는 push에 대한 hook액션을 지원하는데, package에도 동일하게 적용 가능하다. 이것을 이용해 빌드, 배포자동화도 가능할 것 같다.

![image](/images/post_9_git_npm/package_main.png)  
[github - package 메인화면]

## package registry에 등록하기
![image](/images/post_9_git_npm/npm_publish_1.png) 
 
1. package를 먼저 간단히 만든다.  [샘플 package 보기](https://github.com/cjstk7168/hello-world-npm)  
    본 예제에서는 정~말 간단히 작성하였다. 
    ```
    const print = () => {
        console.log('hello world!!');
    };
    ```

2. 생성하였다면 publish를 해주어야 한다.  
    [github 자료 참고](https://github.com/features/package-registry)  
    `npm publish`를 위해서는 저장소에 로그인을 하여야하는데, 
    ```
    npm login --registry=https://npm.pkg.github.com --scope=@${username}
    ```  
    권한설정이 우선되어야한다.  
    [github 관련자료](https://help.github.com/en/articles/configuring-npm-for-use-with-github-package-registry)
    [access token 생성](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line)
    
    위 링크를 참고하여 생성하였다면 `npm login`을 해준다.
    ```
    npm login --registry=https://npm.pkg.github.com --scope=@${username}
    ```
    
    Password는 위에서 생성한 access token을 입력해준다.
    
    login이 되었다면 project내에서 `npm publish`하면 해당 git저장소로 간단히 올라간다.

3. package사용하기 [샘플 프로젝트](https://github.com/cjstk7168/call-github-npm-sample)  
    그 이후에는 일반 npm저장소에 있는것과 마찬가지로 사용이 가능하다.
    `npm install @${username}/${package_name}` 과같이 설치가 가능하다.
    
    위 예제 프로젝트에서는 다음의 명령어로 설치하였다. 
    ```
    npm install --save @cjstk7168/hello-world-npm
    ```
    
    사용할 때는 
    ```
    const { print } = require('@cjstk7168/hello-world-npm');
    print();
    ```
    위와같이 간단하게 사용이 가능하다.
    
    npm저장소는 개인이 사용하기에도 유료라서 아쉬웠는데, github를 이용하면 npm저장소를 무료로 이용가능해서 좋다는 생각이 든다.


4. 결과
    ```
    $node index.js 
    hello world!!
    ```

## reference
1. https://github.com/features/package-registry
2. https://www.44bits.io/ko/post/news--announcing-github-package-registry