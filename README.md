# Blog 빌드 과정

> 개발 환경은 Mac m1 pro 이다. Window 운영체제와 인텔 칩의 Mac과 빌드 과정에서 약간의 차이가 있을 수 있다.

- - -

## 사전세팅

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