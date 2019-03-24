---
title:  "Terminal"
date:   2019-03-21
last_modified_at: 2019-03-24
permalink: /docs/terminal/
toc: false
---
[Mac용 터미널의 키보드 단축키](https://support.apple.com/ko-kr/guide/terminal/trmlshtcts/mac)

삽입점을 명령어 라인의 시작 부분으로 이동
`ctrl + A`

삽입점을 명령어 끝 부분으로 이동
`ctrl + E`

***
디렉토리 파일리스트 조회
```sh
$ ls
```
디렉토리 path 조회
```sh
$ pwd
```
디렉토리 이동
```sh
$ cd path/path/
$ cd ../../ #뒤로 이동
```
디렉토리 생성
```sh
$ mkdir name
```
디렉토리 복사/이동
```sh
# sample.txt를 folder 안으로 복사
$ cp sample.txt folder/sample.txt
# sample.txt를 folder 안으로 이동
$ mv sample.txt folder/sample.txt
```

디렉토리 구조 조회
```sh
# 먼저 tree를 설치해야 합니다.
$ brew install tree

$ tree
```
