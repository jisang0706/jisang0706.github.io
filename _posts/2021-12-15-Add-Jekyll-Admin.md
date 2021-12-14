---
layout: post
title:  "Jekyll-admin 추가 과정"
date:   2021-12-15 01:22:43 +0900
categories: jekyll update
---

> ### Jekyll Admin

블로그의 모든 내용을 터미널을 이용해 작성하기는 어렵다.
Jekyll admin은 블로그의 admin 페이지에서 파일들을 관리하기 위한 플러그인이다.

- - -

### 추가 과정

프로젝트 경로로 들어가면 Gemfile 이라는 파일이 있다.

파일에 해당 코드를 추가한다.

    gem 'jekyll-admin', group: :jekyll_plugins

플러그인 설치를 진행한다.

    bundle install

설치가 완료되면 다시 Jekyll을 실행한다.

    bundle exec jekyll serve

![Alt text](/assets/img/Jekyll-admin-screen.png "Git-admin")   
브라우저에서 `{blog_url}/admin` 으로 접속하니 적용이 잘 됐다!