# Blog 빌드 과정

> 개발 환경은 Mac m1 pro 이다. Window 운영체제와 인텔 칩의 Mac과 빌드 과정에서 약간의 차이가 있을 수 있다.

- - -

## 1. Git 로컬 저장소 생성

1. GitHub에 `<username>.github.io` 형태로 Repository를 만든다.
2. 해당 Repository를 로컬로 클론한다. (GitHub Desktop을 이용해 쉽게 해결했다)
3. 작업할 블로그 공간 생성 완료!

## 2. 사전 준비 및 Jekyll 설치

### 1. gcc 설치

> 기본적으로 깔려 있지만, 해당 작업을 생략할 시 디펜던시 에러가 발생한다.

    brew install gcc

### 2. ruby 시작하기.
> Mac에는 기본적으로 ruby가 깔려 있지만 사용할 수 없다.

```
brew install rbenv ruby-build
```

`zsh`를 사용하기 때문에 `~/.zshrc`에 아래의 코드를 추가한다.
```
eval "$(rbenv init -)"
```

추가한 후, 터미널에 아래의 코드를 입력한다.
환경설정 바꾼것을 적용시켜준다.
```
source ~/.zshrc
```

```
rbenv install 2.7.2
rbenv global 2.7.2
```

```
ruby -v
 -> ruby 2.7.2p137 (2020-10-01 revision 5445e04352) [arm64-darwin21]
```
##### 잘 적용이 됐다!

### 3. Jekyll 구동을 위해 설정하기.
```
gem install bundler jekyll
rbenv rehash
```

설치 후 프로젝트 폴더로 이동하고 아래의 코드를 입력한다.
```
bundle init
bundle add jekyll
jekyll new . --force
```
프로젝트가 생성되었다!

```
bundle exec jekyll serve
```
`localhost:4000`으로 들어가니 잘 작동이 된다

## 3. 테마 적용하기

> `daattali`의 [beautiful-jekyll](https://github.com/daattali/beautiful-jekyll#readme)을 이용했다.

1. 테마를 zip형태로 다운로드한다.
2. 해당 테마를 자신의 기존 블로그 디렉토리에 `_post` 폴더를 제외하고 붙혀넣는다.
3. `_config.yml` 파일을 자신의 블로그 설정에 맞게 수정한다.

##### 적용 끝!

해당 테마는 `_config.yml`의 `social-network-links` 부분의 내용을 수정해 Footer에 표시되는 SNS 정보들을 수정할 수 있다.

가지고 있는게 메일과 깃허브 주소만 있으므로 해당 정보만 입력하고 나머지는 주석 처리를 해주었다.
![Alt text](/assets/img/footer_screen.png "Footer-Screen")

그 밖에도 블로그 소유자, 프로필 사진, 블로그 링크를 이 블로그에 맞게 수정했다.

![Alt text](/assets/img/intro_blog.png "Git-admin")

## 4. 부가 기능 구현하기

### 1. Favicon

> Favicon은 즐겨찾기(favorites)와 아이콘(icon)의 합성어로, 주소창에 조그만 아이콘으로 표시된다.

1. 자신이 favicon으로 설정하고 싶은 16x16 이미지를 ico 파일 형태로 준비한다.
2. 해당 ico 파일을 블로그의 디렉토리에 넣은 후 /_include/head.html 파일 내에 아래의 코드를 입력한다.

```
<link rel="shortcut icon" type="image/x-icon" href="favicon.ico 경로">
<link rel="icon" type="image/x-icon" href="favicon.ico 경로">
```

##### 블로그를 다시 작동시키면 적용이 된다.
![Alt text](/assets/img/favicon_screen.png "Favicon-Screen")

### 2. Disqus

> 작성한 글들에 댓글 기능을 추가한다. 직접 만들 필요 없이 외부 API를 사용해 만들 수 있다!

1. [DISQUS](https://disqus.com)에 가입을 한 후 사이트를 생성한다.
2. `_config.yml` 하단에 다음과 같은 코드를 추가한다.

```
comment:
  provider:       "disqus"
  disqus:
    shortname:    "super-corini"
```

3. `_config.yml`내부의 `comments: false` 부분을 `comments: true`로 바꿔준다.
4. DISQUS 홈페이지에서 Univalsal Code를 복사한다.
5. `/_includes/disqus.html`의 `<script>` 부분을 복사한 코드로 대치한다.

##### 적용 완료!
![Alt text](/assets/img/disqus_screen.png "Disqus-Screen")