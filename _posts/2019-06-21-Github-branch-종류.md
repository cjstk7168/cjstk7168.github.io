---
layout: post
title: "Git branch 종류와 명명규칙"
description: "branch 어떻게 사용할까?"
date: 2019-06-21
categories: [Github]
tags: [Infra, Github]
comments: true
share: true
---

## Github branch 종류
1. `Master`
**배포 Release(Prod) 버전의 소스가 들어있는 branch**
기본적으로 github 저장소를 생성하면 있는 branch이다. 배포이력을 관리하기 위한 용도로 사용한다.

2. `Develop`
**개발버전의 소스가 들어있는 branch**
일반적으로 Master branch에 병합하기 전 최종 개발버전의 소스가 들어있다.
다음 Release될 버전의 소스라고 생각하면 된다.

3. `Feature`
**기능을 개발중인 branch**
개발자들이 기능개발을 위하여 생성/이용 하는 branch이다. 개발이 완료되면 develop와 병합하여 다른 사람들과 공유한다.

4. `Hotfix`
**Master branch의 오류사항을 수정하는 branch**
Feature > Develop > Master의 병합순이 아니라 Master에서 급하게 수정해야하는 경우에 사용한다.
Master에서 직접 branch를 분기하여 생성하며 수정 후 Develop가 아닌 Master에 병합하여 배포한다.  