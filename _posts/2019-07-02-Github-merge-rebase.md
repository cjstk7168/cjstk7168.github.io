---
path: "/14"
layout: post
title: "Git branch 병합하기"
description: "merge 그리고 rebase"
date: 2019-07-02
categories: [Github]
tags: [Infra, Github]
comments: true
share: true
---

## Github merge와 rebase 이해하기
Github를 사용하다보면 branch를 생성하고 add, commit, merge, rebase, push.. 뭔가 할일이 많다.  
공부해야할게 많다. 그 중 병합에 대해 오늘은 끄적여보고자 한다.

**`merge`와 `rebase` 둘 다 2개의 branch를 병합하는 방법이다. 뭐가 다를까?**

## Merge  
간단한 그림으로 알아보고자 한다.  

1. 그림처럼 commit 상태가 있다고 가정해본다.  
이 상태에서 master에서 새로운 feature branch를 생성하여 추가로 작업을 하였다.
```
$git checkout -b feature/sample
$git commit -m "commit a"
$git commit -m "commit b" 
```

그러면 현재의 git object의 상태는 그림과 같다.  
![image](/images/post_6/merge_1.png)


2. 그런데 Master branch에 문제가 생겼다. Hotfix를 해야하는 상황이 생긴것이다.
그래서 그림과 같이 새로운 branch를 생성하여 작업하고 Master와 다시 병합하였다.
```
$git checkout master
$git checkout -b hotfix/typo-err
$git commit -m "hotfix"
$git checkout master
$git merge hotfix/typo-err
```
![image](/images/post_6/merge_2.png)

그럼 위와같이 HEAD가 이동하였고, cli에는 `fast-worward`라는 내용을 확인할 수 있다.  
빨리감기 라고도 하며 branch의 head가 이동했다는것을 의미한다.


3. 이 상태에서 이제 개발이 완료된 feature/sample branch를 master와 병합하고자 한다.
```
$git checkout master
$git merge sample-branch 
```
![image](/images/post_6/merge_3.png)

위와같이 merge를 하게되면 새로운 커밋이 생성되며 갈래가 나갔다가 다시 합쳐지는 형태로 생성되며
새로운 commit이 자동으로 생성된다. (위 그림에서 xxx 커밋)
이러한 형태를 `3-way Merge`라고 부른다.



## Rebase  
간단한 그림으로 알아보고자 한다.  

1. Merge와 동일하게 commit 상태가 있다고 가정해본다.
```
$git checkout -b feature/sample
$git commit -m "commit a"
$git commit -m "commit b" 
```
![image](/images/post_6/rebase_1.png)

2. 이번에도 Master branch에 문제가 생겨서 hotfix를 하였다.
```
$git checkout master
$git checkout -b hotfix/typo-err
$git commit -m "hotfix"
$git rebase master
```
![image](/images/post_6/rebase_2.png)

3. 이 상태에서 이제 개발이 완료된 feature/sample branch를 master와 병합(이번엔 rebase)하고자 한다.
```
$git rebase master 
```
![image](/images/post_6/rebase_3.png)

4. `feature/sample`의 branch꼬리를 master에 가져다 붙였다. 이제 master에서 merge를 하면
깔끔하게 `fast-forward`가 이루어 진다.

![image](/images/post_6/rebase_4.png)


## 결론
merge보다 rebase가 이력관리가 더 깔끔하다. (가지가 나갔다가 들어갔다가 하지않기 때문에).
때문에 실무에서는 rebase가 대부분 사용하고 있는데, 어떤 차이가 있는지 왜 rebase를 쓰는지
조금이나마 이 글을 정리하면서 이해가 되었다.


---
* References  
1. https://cyberx.tistory.com/96