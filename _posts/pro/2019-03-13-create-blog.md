---
title:  "GitHub Pages로 홈페이지 만들기"
date:   2019-03-13
last_modified_at: 2019-03-21
---
[Jekyll 홈페이지](https://jekyllrb-ko.github.io/)를 참고하여 Jekyll 기본 테마로 가장 쉽게 홈페이지를 생성하여 배포하는 과정을 요약한 노트입니다.

## [GitHub Pages Guide](https://pages.github.com/)
[Github](https://github.com/)에서 회원가입하신 후 New repository를 생성합니다. Repository name에 username.github.io를 입력한 후 Create repository를 클릭하시면 됩니다. username에는 본인의 github의 id를 입력해주시면 되는데 아래의 사진을 참고하시면 저는 제 github의 id인 verycys를 입력하였습니다.
{% include figure image_path="/assets/images/posts/create-blog-01.png" %}

맥에서 원하시는 위치에 폴더를 만듭니다. 터미널을 실행시킨 후 해당 디렉토리로 이동합니다. 앞으로는 이 디렉토리를 루트 디렉토리로 명명하겠습니다. 루트 디렉토리로 이동하신 후 터미널에서 아래의 명령을 입력합니다. username은 본인의 username을 입력해주시면 됩니다.

```sh
# 터미널에서 원하는 디렉토리로 이동
$ cd dev/verycys/verycys.github.io

# 디렉토리에서 git clone
$ git clone https://github.com/username/username.github.io
```

## [Jekyll Guide](https://jekyllrb-ko.github.io/docs/installation/)
맥에는 기본적으로 루비가 설치되어 있지만 다른 운영체제를 사용하시는 분들은 시작하기 전에 아래의 사항들을 설치해야 합니다.
- [루비](https://www.ruby-lang.org/en/downloads/) 버전 2.2.5 또는 그 이상. 모든 개발환경 헤더 포함 (루비 설치정보는 `ruby -v` 로 확인할 수 있습니다)
- [RubyGems](https://rubygems.org/pages/download) (명령어 `gem -v` 로 확인할 수 있습니다)
- [GCC](https://gcc.gnu.org/install/) 와 [Make](https://www.gnu.org/software/make/) (명령행 인터페이스에서 `gcc -v` 와 `g++ -v`, `make -v` 로 확인할 수 있습니다)

루비 설치가 완료되면 아래의 명령을 터미널에 입력합니다.
```sh
# RubyGems를 통해 Jekyll과 Bundler를 설치
$ gem install jekyll bundler

# 디렉토리 위치 확인
$ pwd
../dev/verycys/verycys.github.io

# 디렉토리에서 새 Jekyll 사이트 생성
$ jekyll new .

# 디렉토리에 아래와 같은 파일이 생성됨을 확인
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2019-03-13-welcome-to-jekyll.markdown
├── about.md
└── index.md

# 미리보기 서버로 사이트 빌드
$ bundle exec jekyll serve
```
Bundler는 다른 RubyGem들을 관리하는 RubyGem입니다. 각각의 RubyGem이 작동하기 위한 필수 의존요소들을 설치해주기 때문에 언제나 호환되는 버전의 RubyGem을 가지고 있게 됩니다.

Gemfile과 Gemfile.lock은 사이트에 필요한 RubyGem을 Bundler에게 알려주는 역할을 합니다.

`bundle exec jekyll serve`라고 실행하면, Bundler는 Gemfile.lock에 명시된 버전의 RubyGem을 사용해 Jekyll 사이트를 생성하기 때문에 의존성과 호환성에 어떠한 충돌도 발생하지 않습니다.

터미널에서 위의 명령을 모두 입력한 후 브라우저에 `http://localhost:4000`를 입력하면 아래와 같이 홈페이지가 생성된 것을 확인할 수 있습니다. 생성된 홈페이지는 Minima라고 하는 루비 젬 기반 테마가 적용된 페이지인데 추후 이 홈페이지를 더욱 이쁘게 만드는 노트를 작성할 예정입니다.
{% include figure image_path="/assets/images/posts/create-blog-02.png" %}

## Deploy
터미널에서 루트 디렉토리에 위치한 후 아래의 명령을 입력합니다.
```sh
git add .
git commit -m "initial commit"
git push origin master
```
git push를 완료한 후 브라우저에서 `https://username.github.io/`를 입력하면 로컬서버에서 확인한 것과 동일한 홈페이지가 생성되었음을 확인할 수 있습니다. username은 본인의 username으로 변경해주시면 됩니다.
