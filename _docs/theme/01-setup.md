---
title:  "기본환경 셋팅"
date:   2019-03-13
last_modified_at: 2019-03-21
permalink: /docs/setup/
---
## 1. 다운로드
이 가이드는 Jekyll 테마 중 [Minimal-Mistakes][minimal-mistakes-gh] 테마를 적용하여 홈페이지를 만드는 가이드 입니다.
테마를 만든 개발자의 가이드는 다음의 [링크][minimal-mistakes-guide]를 참고하면 됩니다.
오리지널 가이드에서 제가 커스터마이징 한 부분만 기술하였으며 전체를 포괄하지는 않습니다.
먼저 다음의 [링크][minimal-mistakes-releases]에서 최신버전의 소스코드를 다운 받습니다.
제가 다운받은 소스코드는 4.15.2 버전입니다. 다운로드를 완료한 후 아래의 리스트에 있는 파일을 제거합니다.
```
.editorconfig
.gitattributes
.github
/docs
/test
CHANGELOG.md
minimal-mistakes-jekyll.gemspec
README.md
screenshot-layouts.png
screenshot.png
```

마지막으로 다운받은 파일 중 `Gemfile`의 코드를 다 지우고 아래의 코드를 복붙합니다.
```ruby
source "https://rubygems.org"

gem "jekyll", "~> 3.5"
gem "minimal-mistakes-jekyll"
```

## 2. 루비설치
맥에는 기본적으로 루비가 설치되어 있지만 다른 운영체제를 사용하시는 분들은 시작하기 전에 아래의 사항들을 설치해야 합니다.
- [루비](https://www.ruby-lang.org/en/downloads/) 버전 2.2.5 또는 그 이상. 모든 개발환경 헤더 포함 (루비 설치정보는 `ruby -v` 로 확인할 수 있습니다)
- [RubyGems](https://rubygems.org/pages/download) (명령어 `gem -v` 로 확인할 수 있습니다)
- [GCC](https://gcc.gnu.org/install/) 와 [Make](https://www.gnu.org/software/make/) (명령행 인터페이스에서 `gcc -v` 와 `g++ -v`, `make -v` 로 확인할 수 있습니다)

루비 설치가 완료되면 Jekyll과 Bundler의 설치를 위해 다음의 명령을 터미널에 입력합니다.
{: style="text-align: justify;"}
```
$ gem install jekyll bundler
```

## 3. 로컬서버
이제 기본환경 셋팅이 완료되었습니다. 터미널에서 소스코드를 다운받은 폴더(이하 프로젝트 폴더)로 이동한 후 다음의 명령을 입력합니다.
```
$ bundle exec jekyll serve
```
브라우저를 열어 `http://127.0.0.1:4000` 혹은 `localhost:4000`을 입력하면 다음의 화면이 보임을 확인할 수 있습니다.
{% include figure image_path="/assets/images/docs/0101.png" alt="" caption="" %}
이제 홈페이지를 만들 뼈대를 갖추었습니다. 앞으로는 이 뼈대에 살을 붙여보겠습니다.

## 4. 참고문서
[Jekyll-국문][Jekyll-국문]<br/>
[Jekyll-국문-github][Jekyll-국문-github]<br/>
[Jekyll-영문][Jekyll-영문]


[minimal-mistakes-gh]: https://github.com/mmistakes/minimal-mistakes
[minimal-mistakes-releases]: https://github.com/mmistakes/minimal-mistakes/releases
[minimal-mistakes-guide]: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
[Jekyll-국문]: https://jekyllrb-ko.github.io/
[Jekyll-국문-github]: https://github.com/jekyllrb-ko/jekyllrb-ko.github.io
[Jekyll-영문]: https://jekyllrb.com/
