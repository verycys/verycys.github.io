---
title:  "Jekyll Basics"
date:   2019-03-21
last_modified_at: 2019-03-23
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

Layout에 다른 layout을 적용하여 쓸 수도 있습니다. `_layouts` 디렉토리와 그 안에 wrapper.html 파일을 새로 만듭니다. wrapper.html에 다음의 코드를 작성합니다. layout 위 아래에 Wrapper 문구가 표시되도록 하는 코드입니다.
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
<br>
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
저장을 한 후 포스트 페이지를 새로고침하면 다음의 화면이 보임을 확인할 수 있습니다. 즉, 머리말에 layout 값을 입력해주면 현재 layout에 다른 layout을 적용할 수도 있습니다.
{% include figure image_path="/assets/images/posts/jekyll-basics-layouts01.png" %}
- Jekyll 참고링크[^1]
  - [Layouts][13]

## Variables
Jekyll은 작업이 필요한 파일을 찾아 루트 디렉토리를 모두 돌아다닙니다. 작업 대상은 YAML 머리말을 가진 모든 파일입니다. Jekyll은 Liquid tags를 통해 다양한 데이터를 생성합니다. Layouts에서 content도 변수 중 하나입니다. HTML 파일에서 변수를 사용하기 위해서는 아래처럼 변수를 2개의 curly braces[^2]로 감싸줘야 합니다.
{% raw %}
```html
# content 변수 사용
{{ content }}

# page의 제목 사용
{{ page.title }}
```
{% endraw %}
Layout의 머리말에 변수를 따로 설정하면 `layout.variable`도 사용할 수 있습니다.

- Jekyll 참고링크
  - [변수][14]

## Includes
Include tag를 사용하면 `_includes` 디렉토리에 저장된 다른 파일의 내용을 포함시킬 수 있습니다. `_includes` 디렉토리와 그 안에 header.html 파일을 새로 만듭니다. 그리고 header.html에 다음의 코드를 작성합니다.
{% raw %}
```html
<h1>{{ site.title }}</h1>
<hr><br>
```
{% endraw %}
`_layouts` 디렉토리에 있는 wrapper.html 파일을 다음과 같이 수정합니다. 그리고 포스트 페이지를 새로고침하면 header가 포함된 화면이 보임을 확인할 수 있습니다.
{% raw %}
```html
<html>
  <head>
    <meta charset="utf-8">
    <title>Document</title>
  </head>
  <body>
    Wrapper <br>
    {% include header.html %}
    {{ content }}
    <br> Wrapper
  </body>
</html>
```
{% endraw %}
<br>
Include에 파라메터를 사용할 수도 있습니다. 먼저 wrapper.html 파일을 다음과 같이 수정합니다. color="blue" 코드를 추가하였습니다.
{% raw %}
```html
<html>
  <head>
    <meta charset="utf-8">
    <title>Document</title>
  </head>
  <body>
    Wrapper <br>
    {% include header.html color="blue" %}
    {{ content }}
    <br> Wrapper
  </body>
</html>
```
{% endraw %}
그리고 header.html 파일을 다음과 같이 수정합니다. `include.color`는 파라메터로서 wrapper.html과 같이 include tag를 파라메터 값과 함께 호출하면 그 값이 입력됩니다. 즉, 포스트 페이지를 새로고침하면 `include.color`에 blue값이 입력되면서 title이 파란색으로 변한 것을 확인할 수 있습니다.
{% raw %}
```html
<h1 style="color: {{ include.color }}">{{ site.title }}</h1>
<hr><br>
```
{% endraw %}
- Jekyll 참고링크
  - [조각파일][15]

## Looping Through Posts
포스트들의 List를 만드려면 페이지에 다음과 같이 코드를 작성하면 됩니다.
{% raw %}
```html
{% for post in site.posts %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
{% endfor %}
```
{% endraw %}

- Jekyll 참고링크
  - [포스트 작성하기][16]

## Conditionals
포스트에 조건을 설정하려면 페이지에 다음과 같이 코드를 작성하면 됩니다. 아래의 조건은 포스트 list에서 현재 위치한 포스트의 색깔을 붉은색으로 표시하는 겁니다.
{% raw %}
```html
{% for post in site.posts %}
  <li>
    <a style="{% if page.url == post.url %}color: red;{% endif %}"
       href="{{ post.url }}">{{ post.title }}</a>
  </li>
{% endfor %}
```
{% endraw %}

## Data Files
변수뿐만 아니라, Liquid 템플릿 시스템을 통해 접근할 수 있는 자신만의 데이터를 정의할 수 있습니다. Jekyll은 `_data` 디렉토리의 YAML과 json, csv 파일로부터 데이터를 읽어들일 수 있습니다. `site.data`를 통해 이 데이터를 사용할 수 있습니다. 강의에서는 다음과 같이 data 디렉토리와 people.yml 파일을 만든 후 people.yml 파일에 아래의 코드를 작성하였습니다.
```sh
├── _data
│   └── people.yml
```
```yml
- name: "Mike"
  occupation: "Giraffe Academy"

- name: "Steve"
  occupation: "Firefighter"

- name: "Rob"
  occupation: "Programmer"
```
HTML 파일에 다음의 코드를 작성하여 data를 사용할 수 있습니다.
{% raw %}
```html
{% for person in site.data.people %}
  {{ person.name }}, {{ person.occupation }} <br>
{% endfor %}
```
{% endraw %}
- Jekyll 참고링크
  - [데이터 파일][17]

## Static Files
다음과 같은 코드를 페이지에 작성한 후 브라우저를 실행하면 루트 디렉토리에 있는 모든 static file의 path를 로드할 수 있습니다.
{% raw %}
```html
{% for file in site.static_files %}
  {{ file.path }}
{% endfor %}
```
{% endraw %}
<br>
강의에서는 asstes 디렉토리와 그 하위디렉토리로 images 디렉토리를 만든 후 모든 image 파일을 images 디렉토리로 이동시켰습니다. 그리고 Jekyll에 images 디렉토리 안에 있는 모든 파일은 image라는 것을 인식시키기 위해 `_config.yml` 파일에 다음과 같은 코드를 작성하였습니다.
```yml
-
defaults:
  scope:
    path: "assets/images"
  values:
    image: true
```
그리고 다음과 같은 코드를 페이지에 작성한 후 브라우저를 실행하면 images 디렉토리 안에 있는 모든 image가 로드되는 것을 확인할 수 있습니다.
{% raw %}
```html
{% for file in site.static_files %}
  {% if file.image %}
    <img src="{{ file.path }}" alt="{{ file.name }}">
  {% endif %}
{% endfor %}
```
{% endraw %}
- Jekyll 참고링크
  - [정적 파일][18]


## Hosting in Github Pages
Github Pages는 개인이나 단체 또는 저장소를 위한 공개 웹 페이지로서, Github가 제공하는 github.io 도메인이나 자신만의 도메인에 자유롭게 호스팅할 수 있습니다. 먼저 Github에서 새 repository를 만듭니다. 그리고 `_config.yml` 파일의 baseurl에 repository name을 입력합니다.

터미널에 다음의 명령어를 순차적으로 입력합니다.
```sh
$ git init
$ git checkout -b gh-pages
$ git add .
$ git commit -m "initial commit"
# verycys를 your github id로 jekyll-basics를 your repository name으로 변경하면 됩니다.
$ git remote add origin https://github.com/verycys/jekyll-basics.git
$ git push origin gh-pages
```
로컬 repository에 있던 파일들이 모두 Github에 업로드 되었습니다. Github repository에서 Settings를 클릭한 후 Github Pages 부분을 보면 다음과 같이 사이트 url을 확인할 수 있습니다.
{% include figure image_path="/assets/images/posts/jekyll-basics-deploy01.png" %}
해당 url을 클릭하면 로컬 서버에서 보았던 사이트와 동일한 사이트가 호스팅 된 것을 볼 수 있습니다. 앞으로 로컬에서 사이트를 수정하면 터미널에서 다음의 명령어를 입력해야 배포된 사이트에도 적용이 됩니다.
```sh
$ git add .
$ git commit -m "Whatever you want"
$ git push origin gh-pages
```
<br>
사이트 생성부터 배포까지 모두 완료되었습니다. 수고하셨습니다!
- Jekyll 참고링크
  - [Github Pages 배포][19]

## 각주

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
[14]: https://jekyllrb-ko.github.io/docs/variables/
[15]: https://jekyllrb-ko.github.io/docs/includes/
[16]: https://jekyllrb-ko.github.io/docs/posts/
[17]: https://jekyllrb-ko.github.io/docs/datafiles/
[18]: https://jekyllrb-ko.github.io/docs/static-files/
[19]: https://jekyllrb-ko.github.io/docs/github-pages/

[^1]: Jekyll 영문버전에서 Layouts부분은 국문버전에서 없습니다.
[^2]: { }를 curly braces라고 합니다.
