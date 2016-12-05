---
layout: post
title: "push 시 error 403 해결방법"
description: "git push 할때 error 403 해결방법 메모"
date: 2016-12-01
tags: [git, github, push, error]
comments: true
share: true
---

나는 IDE에 내장된 git 기능이나 git bash로 버전관리를 하는데 가끔 push 할때마다 error:403 이 나곤한다. remote 권한이 없을때 나타나는 error인데 git bash에서 명령어를 입력한다.

#### Git 명령어

<code>$ git remote set-url origin https://username:userpassword@github.com/user/.git</code> 으로 remote(원격저장소)의 url을 변경해준 뒤에,
<code>$ git push origin master</code> 푸시 해주면 끝이다.

***

#### 참고 링크

- [github push를 할때 403에러가 발생하때!!](http://djdotdata.blogspot.kr/2013/05/github-push-403.html#!/2013/05/github-push-403.html)
- [Pushing to Git returning Error Code 403 fatal: HTTP request failed](http://stackoverflow.com/questions/7438313/pushing-to-git-returning-error-code-403-fatal-http-request-failed)
