---
title:  "Jekyll Basics"
date:   2019-03-21
last_modified_at: 2019-03-21
---
이 강의노트는 Youtube에서 [Mike Dane - Jekyll Basics][1]를 보고 작성하였습니다.

## Introduction
강의과정에 대한 개략적인 설명에 대한 영상입니다.

## Mac Installation
Jekyll을 설치하기 위해서는 2가지 프로그램이 필요합니다. 하나는 Ruby로 Ruby는 프로그래밍 언어이며 Jekyll은 루비를 사용하여 작성되었습니다. 다른 하나는 RubyGems입니다. RubyGems는 Ruby의 패키지 매니저 입니다. 맥에는 위의 2가지 프로그램이 처음부터 설치되어 있습니다.

터미널에서 `ruby -v`과 `gem -v`를 입력하면 현재 설치된 Ruby와 RubyGems의 버전을 확인할 수 있습니다. Ruby와 RubyGems가 설치되어 있으면 터미널에서 `gem install jekyll bundler`를 입력합니다. 이 명령은 RubyGems에게 맥에 Jekyll을 설치하도록 요청합니다. 설치가 완료된 후 터미널에 `jekyll -v`를 입력하면 설치된 Jekyll의 버전을 확인할 수 있습니다.

모든 설치가 완료되었습니다. 이제 당신의 컴퓨터로 사이트를 만들 모든 준비가 되었습니다.

## Windows Installation
저는 macOS를 사용하므로 Pass하였습니다.

## Creating a Site
터미널에서 원하는 디렉토리로 이동한 후 `jekyll new .`를 입력하면 해당 디렉토리에서 사이트를 만드는 기본파일(Default contents)들이 생성됩니다. 생성된 사이트를 로컬에서 확인하고 싶을 때는 터미널에 `bundle exec jekyll serve`를 입력합니다. 사이트를 만들고 처음 로컬서버를 실행할 때는 `bundle exec jekyll serve`를 입력하지만 이후부터는 `jekyll serve`만 입력해도 서버가 실행됩니다. 서버 실행 후 브라우저에 `http://127.0.0.1:4000/`를 입력하면 생성한 사이트를 로컬에서 확인할 수 있습니다.

기본파일들은 다음의 구조를 가집니다. 이러한 파일들을 포함하는 최상위 디렉토리를 루트 디렉토리라고 부르겠습니다.
```sh
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2019-03-13-welcome-to-jekyll.markdown
├── about.md
└── index.md
```
- `_posts`: 모든 블로그 포스트를 저장해 두는 디렉토리 입니다. YEAR-MONTH-DAY-title.MARKUP과 같이 파일 명명규칙을 따라야 합니다.
- `config.yml`: 환경설정 정보를 보관합니다. yml파일은 Key value pair나 variables 등을 저장하는 language입니다.
- `Gemfile`: 블로그의 모든 dependencies를 저장합니다.
- Jekyll 참고링크
  - [빠른시작 설명서][2]
  - [디렉토리 구조][3]

## Front Matter
각 포스트의 FrontMatter(머리말)은 시작과 끝을 대시문자(-) 세 개로 감싸서 올바른 YAML 형식으로 작성해야 합니다. 기본적인 구조는 다음과 같습니다. 대시문자 사이에 사전적으로 정의된 변수를 사용할 수 있고 자신만의 고유한 변수를 정의하는 것도 가능합니다.
```sh
---
layout
title
data
categories
---
```
- layout: 사용할 레이아웃 파일을 지정합니다. 레이아웃 파일은 반드시 `_layouts` 디렉토리에 존재해야 합니다.
- categories: categories에 기재된 문자는 url에 포함됩니다.
- Jekyll 참고링크
  - [머리말][4]

## Writing Posts
기본적으로 작성한 포스트는 `_posts` 안에 위치해야 합니다. 포스트는 일반적으로 마크다운이나 HTML로 작성됩니다. 포스트의 파일명은 `YEAR-MONTH-DAY-title.md` 의 형식에 맞춰야 합니다. `_posts` 안에서 하위 디렉토리를 만들어 포스트들을 관리하는 것도 가능합니다.
- Jekyll 참고링크
  - [포스트 작성하기][5]

## Working With Drafts
포스트를 작성하다가 아직 완성되지 않아 포스트 리스트에 포함되지 않기를 바랄 수도 있습니다. 그럴 때는 루트 디렉토리에 `_drafts` 디렉토리를 만든 후 그 안에 포스트를 위치시키면 `_drafts` 안에 있는 포스트들은 포스트 리스트에 포함되지 않습니다. Draft를 포함하여 사이트를 미리보기 하려면 `jekyll serve --draft`와 같이 터미널에 `--drafts`를 추가하여 명령어를 입력하면 됩니다.

## Creating Pages
페이지를 생성하는 방법에는 두 가지가 있습니다. 사이트의 루트 디렉토리에 각 페이지 별로 HTML이나 마크다운 파일을 만들거나 하위 디렉토리를 만들어 페이지 파일들을 넣어두는 방법입니다. `_layouts` 와 `_includes` 는 사이트 안에 있는 모든 HTML에서 사용할 수 있습니다.
- Jekyll 참고링크
  - [페이지 생성하기][6]

## Permalinks
Permalinks는 Permanent link를 의미합니다. 기본적으로 포스트를 생성하면 YEAR-MONTH-DAY-title로 url이 생성되는데 Permalinks를 지정해주면 지정된 url이 생성됩니다.
- Jekyll 참고링크
  - [고유주소][7]

## Front Matter Defaults
매번 포스트를 작성할 때마다 다음과 같이 머리말을 작성해줘야 합니다. date나 title은 포스트마다 다를 수 있지만 layout이나 permalink 등은 포스트마다 같을 수 있습니다. 이렇게 같은 머리말에 대해 default로 정해주면 반복적으로 작성해야 하는 번거로움을 피할 수 있습니다.
```sh
---
layout: "post"
title: "Sample Post"
date: 2019-03-21
categories: jekyll ruby gem
permalink: /:categories/:title/
---
```
만약 포스트를 `_posts`의 하위 디렉토리인 `dir1`에 저장한다고 해봅시다. `dir1` 안에 있는 모든 포스트의 layout은 post라고 한다면 `_config.yml`에 다음과 같이 작성하여 default값을 정할 수 있습니다.
```sh
defaults:
  # _posts/dir1
  - scope:
      path: "_posts/dir1"
      type: "posts" # optional: pages, posts, drafts 등 사이트 내 콜렉션 이름 사용 가능
    values:
      layout: post # author, permalink 등 여러 개 정의 가능
```
values의 범위를 scope에 존재하는 모든 파일로 제한하고 있습니다. 만약 path에 ""같이 빈 값을 넣는다면 모든 루트 디렉토리에 있는 파일에 values 값이 적용됩니다. 그러나 default값이 정의되어 있더라도 개별 포스트에서 다른 값을 지정하면 개별 포스트에서 지정한 값으로 덮어쓸 수 있습니다.
- Jekyll 참고링크
  - [머리말 기본값][8]

## Themes
`jekyll new .`으로 사이트 생성을 했으면 기본적으로 minima 테마가 적용되어 있습니다. 이 테마를 바꾸고 싶으면 [RubyGems][9]에서 원하는 테마를 검색합니다. 강의에서는 [jekyll-theme-hacker][10] 테마를 예시로 보여줍니다. 테마를 적용하기 위해 먼저 `Gemfile`에 `gem "jekyll-theme-hacker"` 코드를 추가합니다. 그리고 나서 테마 설치를 위해 터미널에 다음의 명령어를 입력합니다.
```sh
$ bundle install
```
테마 설치를 완료한 후 `_config.yml` 파일에 `theme: jekyll-theme-hacker` 코드를 추가합니다. 그리고 테마 적용을 위해 터미널에 다음의 명령어를 입력합니다.
```sh
$ bundle exec jekyll serve
```
명령어를 입력하면 터미널에 Build Warning이 보입니다. 그 이유는 minima 테마는 post, page, home 등의 layout을 사용하는데 hacker 테마는 default와 post layout을 사용합니다. 어떤 layout을 사용하는지는 hacker 테마의 [github][11]에서 확인할 수 있습니다. 따라서 기존 파일들(포스트, 페이지 등)의 layout을 default나 post로 변경해주면 로컬사이트에서 테마가 변경된 것을 확인할 수 있습니다.

- Jekyll 참고링크
  - [테마][12]

## Layouts
Layout은 HTML로 작성된 홈페이지의 기본 골격입니다. 루트 디렉토리에 `_layouts` 디렉토리를 만든 후 그 안에 layout파일들을 위치시키면 포스트나 페이지를 생성할 때 해당 layout을 가져다 쓸 수 있습니다. 강의에서는 다음과 같이 layouts 디렉토리와 post.html 파일을 만든 후 post.html 파일에 아래의 코드를 작성하였습니다.
```sh
├── _layouts
│   └── post.html
```
{% raw %}
```html
<h1>This is a post</h1>
<hr>
{{ content }}
```
{% endraw %}
기존의 포스트를 다시 보면 새로 작성된 post layout이 적용된 것을 확인할 수 있습니다.

Layout에 다른 layout을 적용하여 쓸 수도 있습니다. `_layouts` 디렉토리에 wrapper.html 파일을 새로 만듭니다. wrapper.html에 다음의 코드를 작성합니다. layout 위 아래에 Wrapper 문구가 표시되도록 하는 코드입니다.
{% raw %}
```html
<html>
  <head>
    <meta charset="utf-8">
    <title>Document</title>
  </head>
  <body>
    Wrapper <br>
    {{ content }}
    <br> Wrapper
  </body>
</html>
```
{% endraw %}
그리고 post.html을 다음과 같이 작성합니다.
{% raw %}
```html
---
layout: "wrapper"
---
<h1>This is post</h1>
<hr>
{{ content }}
```
{% endraw %}
저장을 한 후 포스트 페이지를 새로고침하면 다음의 화면이 출력됨을 확인할 수 있습니다. 즉, 머리말에 layout 값을 입력해주면 현재 layout에 다른 layout을 적용할 수도 있습니다.
{% include figure image_path="/assets/images/posts/jekyll-basics-layouts01.png" %}
- Jekyll 참고링크(Layouts은 국문사이트가 없습니다.)
  - [Layouts][13]

## Variables
다시보며 정리해야함

## Includes
다시보며 정리해야함

## Looping Through Posts
home.html 생성하면 index 레이아웃이 됨.
포스트 나열하는 거 배움  
다시 볼 필요없음.

## Conditionals
post.html에 if 조건문 추가함  
다시 볼 필요없음.

## Data Files
data 폴더 생성, data를 home.html에 끌고오는거 함, large data를 활용할 때 유용  
다시 볼 필요없음.

## Static Files
asstes/img 폴더 생성, yml 파일에 defaults 추가, home.html에 이미지 끌어오는거 함  
다시 볼 필요없음.

## Hosting in Github Pages
다시보며 정리해아함  
git checkout -b gh-pages

[1]: https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB
[2]: https://jekyllrb-ko.github.io/docs/quickstart/
[3]: https://jekyllrb-ko.github.io/docs/structure/
[4]: https://jekyllrb-ko.github.io/docs/frontmatter/
[5]: https://jekyllrb-ko.github.io/docs/posts/
[6]: https://jekyllrb-ko.github.io/docs/pages/
[7]: https://jekyllrb-ko.github.io/docs/permalinks/
[8]: https://jekyllrb-ko.github.io/docs/configuration/#front-matter-defaults
[9]: https://rubygems.org/
[10]: https://rubygems.org/gems/jekyll-theme-hacker
[11]: https://github.com/pages-themes/hacker/tree/master/_layouts
[12]: https://jekyllrb-ko.github.io/docs/themes/
[13]: https://jekyllrb.com/docs/layouts/
