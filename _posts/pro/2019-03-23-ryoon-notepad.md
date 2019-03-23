---
title:  "Ryoon Notepad 만들기"
date:   2019-03-23
last_modified_at: 2019-03-23
---
개발공부를 시작하면서 여러 강의를 수강하고 관련 서적을 읽었음에도 머리속에 잘 정리가 되지 않는다는 느낌을 받았습니다. 그래서 제가 보고 배운것들을 잘 정리하여 언제든 사용할 수 있는 자료로 만들고자 Notepad를 만들게 되었습니다.

이 노트는 Jekyll 테마 중 [Minimal-Mistakes][1] 테마를 적용하여 홈페이지를 만드는 과정을 기술한 것입니다. 테마 개발자 가이드에서 제가 커스터마이징 한 부분만 기술하였으며 전체를 포괄하지는 않습니다.
- 참고문서: [테마 개발자 가이드][2], [Jekyll 영문가이드][9], [Jekyll 국문가이드][10]

## Installation
MacOS에는 기본적으로 루비가 설치되어 있지만 다른 운영체제를 사용하시는 분들은 시작하기 전에 아래의 사항들을 설치해야 합니다.
- [Ruby][3] 버전 2.2.5 또는 그 이상. 모든 개발환경 헤더 포함 (루비 설치정보는 `ruby -v` 로 확인할 수 있습니다)
- [RubyGems][4] (명령어 `gem -v` 로 확인할 수 있습니다)
- [GCC][5] 와 [Make][6] (명령행 인터페이스에서 `gcc -v` 와 `g++ -v`, `make -v` 로 확인할 수 있습니다)
- 참고문서: [Jekyll 설치가이드][7]

루비 설치가 완료되면 Jekyll과 Bundler의 설치를 위해 다음의 명령을 터미널에 입력합니다.
```
$ gem install jekyll bundler
```

## Quick Start
먼저 [Minimal-Mistakes Releases][8]에서 최신버전의 소스코드를 다운 받습니다. 다운받은 곳의 디렉토리를 루트 디렉토리로 명명하겠습니다. 제가 다운받은 소스코드는 4.15.2 버전입니다. 다운로드를 완료한 후 아래의 리스트에 있는 파일을 제거합니다.
```sh
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
다운받은 파일 중 `Gemfile`의 코드를 다 지우고 아래의 코드를 작성합니다.
```ruby
source "https://rubygems.org"

gem "jekyll", "~> 3.5"
gem "minimal-mistakes-jekyll"
```
<br>
이제 기본환경 셋팅이 완료되었습니다. 터미널에서 루트 디렉토리로 이동한 후 다음의 명령을 입력합니다.
```sh
$ cd to/your/root/directory
$ bundle exec jekyll serve
```
브라우저를 열어 `http://127.0.0.1:4000` 혹은 `localhost:4000`을 입력하면 다음의 화면이 보임을 확인할 수 있습니다.
{% include figure image_path="/assets/images/posts/ryoon-notepad-01.png" %}

## Structure
Quick Start에서 언급한 필요없는 파일들을 모두 지운 후의 루트 디렉토리의 구조는 다음과 같습니다.
```sh
# 디렉토리에 아래와 같은 파일이 생성됨을 확인
├── _data # 목차설정 및 각 국가별 언어로 자동번역 할 수 있는 data 파일이 있습니다.
├── _includes # layout에 포함될 여러 조각파일들이 있습니다.
├── _layouts # 페이지의 기본구조를 결정하는 layout이 있습니다.
├── _sass # 페이지의 미적기능을 담당하는 scss 파일들이 있습니다.
├── _site
├── .sass-cache
├── assets # css, js, image 파일 등을 저장할 수 있습니다.
├── _config.yml # 홈페이지의 전반적인 환경설정을 담당하는 파일입니다.
├── .gitignore # git repository에 push할 때 제외할 파일들의 목록입니다.
├── .travis.yml
├── banner.js
├── Gemfile
├── Gemfile.lock
├── index.html # 홈페이지의 메인화면을 담당하는 파일입니다.
├── LICENSE
├── package-lock.json
├── Rakefile
└── staticman.yml
```

## Configuration
사이트 전체의 환경설정을 관리하는 파일은 `_config.yml` 입니다. 이 파일의 자세한 설명은 테마 개발자 가이드에서 Configuration 부분을 참고하면 됩니다. 다음은 제가 설정한 값입니다. 설명이 필요한 부분은 주석을 추가하였습니다. default에서 변경하지 않은 부분들은 제외하였습니다.
```yml
minimal_mistakes_skin: "contrast" # air, aqua 등 여러 값이 있으니 테마 개발자 가이드에서 원하는 스킨을 선택하면 됩니다.

# Site Settings
locale: "ko-KR" # 사이트 전체의 언어설정을 위한 부분입니다.
title: "RYOON NOTEPAD"
title_separator: #
name: "Ryoon"
description: "개발자가 되기 위한 공부과정을 작성한 노트입니다."
url: "https://verycys.github.io" # 사이트 url입니다.
baseurl: # the subpath of your site, e.g. "/blog"
repository: "verycys/verycys.github.io" # GitHub username/repo-name

# true로 변경하면 사이트 안에서 현재 어디에 위치해 있는지를 보여줍니다.
breadcrumbs: true # true, false (default)

# 사이트 내 포스트를 검색할 수 있도록 하기 위해 true로 변경하였습니다.
search: true # true, false (default)
search_full_content: true # true, false (default)
search_provider: # lunr (default), algolia, google

# Analytics
# 구글 Analytics 적용할 때 다음의 값만 입력하면 됩니다.
analytics:
  provider: "google" # false (default), "google", "google-universal", "custom"
  google:
    tracking_id: "UA-134102600-2"
    anonymize_ip: # true, false (default)

# Site Footer
footer:
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:verycys@gmail.com"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/verycys"

# Collections
# Documentation 셋팅을 위해 추가하였습니다.
collections:
  docs:
    permalink: "/:collection/:path/"
    output: true

# Defaults
# 각 머리말의 default값을 설정한 것입니다.
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      toc: true
      toc_sticky: true
      permalink: /:categories/:title/
      author_profile: false
      read_time: false
      comments: false
      share: false
      related: false
  # _posts/lec
  - scope:
      path: "_posts/lec"
      type: posts
    values:
      category: LectureNote
      sidebar:
        nav: "lec"
  # _posts/pro
  - scope:
      path: "_posts/pro"
      type: posts
    values:
      category: ProjectNote
      sidebar:
        nav: "pro"
  # _posts/boo
  - scope:
      path: "_posts/boo"
      type: posts
    values:
      category: BookNote
      sidebar:
        nav: "boo"
  # _pages
  - scope:
      path: "_pages"
      type: pages
    values:
      layout: single
      author_profile: false
  # _docs
  - scope:
      path: "_docs"
      type: docs
    values:
      layout: single
      read_time: false
      author_profile: false
      share: false
      comments: false
      toc: true
      toc_sticky: true
      sidebar:
        nav: "docs"
  # assets/images안에 있는 모든 파일이 image라는 것을 인식시키기 위해 셋팅했습니다.
  -
    scope:
      path: "assets/images"
    values:
      image: true
```

## Index.html
먼저 루트 디렉토리에 `_posts` 디렉토리를 만든 후 포스트 하나를 만듭니다. 그리고 `assets` 디렉토리에서 하위 디렉토리로 `images` 디렉토리를 만든 후 Index페이지에 활용할 사진을 넣어둡니다. 마지막으로 루트 디렉토리에 있는 index.html을 다음과 같이 수정합니다. index.html의 구조를 변경하고 싶으면 `layouts` 디렉토리의 home.html 파일을 수정하면 됩니다.
```yml
---
title: "your title"
layout: home
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/your-image.jpg

excerpt: "your excerpt"
---
```

## Navigation



[1]: https://github.com/mmistakes/minimal-mistakes
[2]: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
[3]: https://www.ruby-lang.org/en/downloads/
[4]: https://rubygems.org/pages/download
[5]: https://gcc.gnu.org/install/
[6]: https://www.gnu.org/software/make/
[7]: https://jekyllrb-ko.github.io/docs/installation/
[8]: https://github.com/mmistakes/minimal-mistakes/releases
[9]: https://jekyllrb.com/
[10]: https://jekyllrb-ko.github.io/
