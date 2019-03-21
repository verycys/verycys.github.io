---
title:  "Jekyll Basics"
date:   2019-03-13
last_modified_at: 2019-03-21
---
이 강의노트는 Youtube에서 [Mike Dane - Jekyll basics](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB)를 보고 작성하였습니다.

### 1. 강의소개
강의계획에 대한 소개영상

### 2. 환경셋팅(MacOS)
Jekyll을 설치하기 위해서는 2가지 프로그램이 필요합니다. 하나는 Ruby로 Ruby는 프로그래밍 언어이며 Jekyll은 루비를 사용하여 작성되었습니다. 다른 하나는 RubyGems입니다. RubyGems는 Ruby의 패키지 매니저 입니다. 맥에는 위의 2가지 프로그램이 처음부터 설치되어 있습니다.

터미널에서 `ruby -v`과 `gem -v`를 입력하면 현재 설치된 Ruby와 RubyGems의 버전을 확인할 수 있습니다. Ruby와 RubyGems가 설치되어 있으면 터미널에서 `gem install jekyll bundler`를 입력합니다. 이 명령은 RubyGems에게 맥에 Jekyll을 설치하도록 요청합니다. 설치가 완료된 후 터미널에 `jekyll -v`를 입력하면 설치된 Jekyll의 버전을 확인할 수 있습니다.

모든 설치가 완료되었습니다. 이제 당신의 컴퓨터로 사이트를 만들 모든 준비가 되었습니다.

### 3. 환경셋팅(Window)
Window 환경셋팅영상

### 4. 사이트생성 및 폴더구조 설명
터미널에서 원하는 디렉토리로 이동한 후 `jekyll new .`를 입력하면 해당 디렉토리에서 사이트를 만드는 기본파일(Default contents)들이 생성됩니다. 생성된 사이트를 로컬에서 확인하고 싶을 때는 터미널에 `bundle exec jekyll serve`를 입력합니다. 사이트를 만들고 처음 로컬서버를 실행할 때는 `bundle exec jekyll serve`를 입력하지만 이후부터는 `jekyll serve`만 입력해도 서버가 실행됩니다. 서버 실행 후 브라우저에 `http://127.0.0.1:4000/`를 입력하면 생성한 사이트를 로컬에서 확인할 수 있습니다.

기본파일들은 다음의 구조를 가집니다.
```sh
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2019-03-13-welcome-to-jekyll.markdown
├── about.md
└── index.md
```
- `_posts`: 모든 블로그 포스트를 저장해 두는 폴더 입니다. YEAR-MONTH-DAY-title.MARKUP과 같이 파일 명명규칙을 따라야 합니다.
- `config.yml`: 환경설정 정보를 보관합니다. yml파일은 Key value pair나 variables 등을 저장하는 language입니다.
- `Gemfile`: 블로그의 모든 dependencies를 저장합니다.
- 참고링크
  - [사이트생성](https://jekyllrb-ko.github.io/docs/quickstart/)
  - [폴더구조](https://jekyllrb-ko.github.io/docs/structure/)

### 5. 머리말
각 포스트의 FrontMatter(머리말)은 시작과 끝을 대시문자 세 개로 감싸서 올바른 YAML 형식으로 작성해야 합니다. 기본적인 구조는 다음과 같습니다. 대시문자 사이에 사전적으로 정의된 변수를 사용할 수 있고 자신만의 고유한 변수를 정의하는 것도 가능합니다.
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
- 참고링크
  - [머리말](https://jekyllrb-ko.github.io/docs/frontmatter/)

### 6. 포스트

### 7. [Working With Drafts](https://www.youtube.com/watch?v=X8jXkW3k2Jg&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=7)
jekyll serve --draft

### 8. [Creating Pages](https://www.youtube.com/watch?v=1na-IWfv08M&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=8)

### 9. [Permalinks](https://www.youtube.com/watch?v=938jDG_YPdc&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=9)

### 10. [Front Matter Defaults](https://www.youtube.com/watch?v=CLCaJJ1zUHU&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=10)

### 11. [Themes](https://www.youtube.com/watch?v=NoRS2D-cyko&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=11)
다시보며 정리해야함

### 12. [Layouts](https://www.youtube.com/watch?v=bDQsGdCWv4I&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=12)
다시보며 정리해야함

### 13. [Variables](https://www.youtube.com/watch?v=nLJBF2KiOZw&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=13)
다시보며 정리해야함

### 14. [Includes](https://www.youtube.com/watch?v=HfcJeRby2a8&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=14)
다시보며 정리해야함

### 15. [Looping Through Posts](https://www.youtube.com/watch?v=6N1X5XffuUA&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=15)
home.html 생성하면 index 레이아웃이 됨.
포스트 나열하는 거 배움

### 16. [Conditionals](https://www.youtube.com/watch?v=iNZBEki_x6o&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=16)
post.html에 if 조건문 추가함

### 17. [Data Files](https://www.youtube.com/watch?v=M6b0KmLB-pM&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=17)
data 폴더 생성
data를 home.html에 끌고오는거 함, large data를 활용할 때 유용

### 18. [Static Files](https://www.youtube.com/watch?v=knWjmVlVpso&index=18&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB)
asstes/img 폴더 생성
yml 파일에 defaults 추가
home.html에 이미지 끌어오는거 함

### 19. [Hosting in Github Pages](https://www.youtube.com/watch?v=fqFjuX4VZmU&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=19)
git checkout -b gh-pages
