---
layout: post
title:  "Algorithm-java"
date:   2022-03-17 14:46:54 +0900
categories: jekyll update
---

# check 


# 1주차


## Markdown 이해
- [Github-markdown-docs](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)



## Ruby 설치
- [Ruby](https://www.ruby-lang.org/ko/documentation/installation/)

## Ruby permission ERROR

- [Gem::FilePermissionError](https://jojoldu.tistory.com/288)

## jekyll 설치

- [jekyll](https://jekyllrb.com/)

- [local server](http://127.0.0.1:4000/)

## intelliJ IDEA 설치
- [intelliJ IDEA](https://www.jetbrains.com/ko-kr/idea/)
- 자바 빌드 구성 용이

## 과제 - 마크다운을 이용하여 관심있는 주제에 대해 포스트 작성 후, 지킬을 이용해 로컬 서버에 업로드하기

-  my-awesome-site
- `bundle exec jekyll serve`
- [Server address](http://127.0.0.1:4000/)

- **vs code 에서 수정후 저장 하면 local 에서 바로 확인 가능**


---

# 2주차


## Algorithm analysis

- https://www.edx.org/

### Space complexity

- 알고리즘을 위해 필요한 메모리의 크기

### Time complexity
- 알고리즘을 위해 필요한 연산의 횟수

- 일반적으로 알고리즘 문제 풀이에서의 복잡도는 시간 복잡도를 의미 한다.

### Big O notation

- O(n) 입력에 따라 프로그램의 실행 시간을 대략적으로 나타내는 방법  

## etc

### brew



- [brew](https://brew.sh/index_ko)


- 패키지 관리자
- Homebrew는 Apple(또는 Linux 시스템)에서 제공하지 않는 것들을 설치합니다.

### CRLF


- [CRLF](https://developer.mozilla.org/en-US/docs/Glossary/CRLF)




- CR와 LF를 합성한 단어


- CR = Carriage Return (\r, 0x0D in hexadecimal, 13 in decimal) — moves the cursor to the beginning of the line without advancing to the next line.


- LF = Line Feed (\n, 0x0A in hexadecimal, 10 in decimal) — moves the cursor down to the next line without returning to the beginning of the line.


- A CR immediately followed by a LF (CRLF, \r\n, or 0x0D0A) moves the cursor down to the next line and then to the beginning of the line.





### VS code

- [VS code](https://code.visualstudio.com/)



- `brew install --cask visual-studio-code`
- `[cmd] + shift + p` > markdown preview

### notion

- [notion](https://www.notion.so/)



- Notion은 프로젝트 관리 및 메모 작성 소프트웨어
- Notion은 회사 또는 조직의 구성원이 효율성과 생산성을 위해 마감일, 목표 및 할당을 조정할 수 있도록 설계된 소프트웨어


### craft

- [craft](https://www.craft.do/)

### Kanban board

- Kanban board는 개인적인 수준에서나 조직적인 수준에서 작업을 관리하기 위해 간반을 구현하기 위해 사용할 수 있는 도구들 가운데 하나이다.

## cli 명령어

- `cd` dir 이동

- `.`  현재폴더
- `..` 상위폴더

## Git / Github / Pages


* git : 협업, 로컬 저장소, 버전관리시스템(vcs)

* github : 협업툴, 온라인 저장소 , 버전관리시스템(vcs)

* github pages : jekyll 업로드 > 웹 호스팅 무료


- **Repository name 은 반드시 'DAEHEE97.github.io' 설정해야 함**



## 명령어

### 저장소 초기화

- `git init [directory]`  

- `git clone [repository/link] [directory/저장할 저장소]`




### 버전 관리 (업데이트)

- `git pull` : 온라인 저장소 -> 로컬 저장소 다운로드

- `git add [file...]`  : 커밋할 파일들 스테이징

- `git commit -m ["message"]`  : 스테이징 파일 -> 버전 업데이트

- `git push` : 로컬 저장소 > 온라인 저장소로 업로드

- `git merge` : 충돌 방지를 위해 브렌치 작업, 충돌한걸 해결 해야 함

### 상태

- `git status`
- `git log`

### 내리기

- Changes to be committed: (use "git rm --cached file..." to unstage)

- `git rm --cached <file>`


### .gitignore 파일
-  .gitignore 파일에 스테이징 하지 않을 파일명 폴더명 작성


### etc

- `git clone` ( initialize ) <> `git pull` ( update )




- `git --config global user.name`, `git --config global email` : 사용자명 이메일주소 협업시 log, check 용


- 제일 처음 push 할때는 `git remote add `


- `git remote add origin https://github.com/DAEHEE97/ttt.git`

- remote : online
- origin : local



### Github ERROR

- ['GitHub push token' ERROR](https://hyeo-noo.tistory.com/184)


-  ['! [rejected] main -> main (non-fast-forward) ERROR](https://somjang.tistory.com/entry/Git-rejected-master-master-non-fast-forward-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95)





## 과제 - 마크다운을 이용하여 수업 내용 및 추가 관련내용 정리하여 포스트 작성 후, 지킬을 이용해 로컬 서버에 업로드 후, online 깃허브 페이지 업로드

### ERROR

```
(base) daeheehan@DAEHEEui-MacBookPro _posts % git push
To https://github.com/DAEHEE97/DAEHEE97.github.io.git
 ! [rejected]        main -> main (non-fast-forward)
error: 레퍼런스를 'https://github.com/DAEHEE97/DAEHEE97.github.io.git'에 푸시하는데 실패했습니다
힌트: 현재 브랜치의 끝이 리모트 브랜치보다 뒤에 있으므로 업데이트가
힌트: 거부되었습니다. 푸시하기 전에 ('git pull ...' 등 명령으로) 리모트
힌트: 변경 사항을 포함하십시오.
힌트: 자세한 정보는 'git push --help'의 "Note about fast-forwards' 부분을
힌트: 참고하십시오.

```


```
(base) daeheehan@DAEHEEui-MacBookPro _posts % git push origin main


To https://github.com/DAEHEE97/DAEHEE97.github.io.git
 ! [rejected]        main -> main (non-fast-forward)
error: 레퍼런스를 'https://github.com/DAEHEE97/DAEHEE97.github.io.git'에 푸시하는데 실패했습니다
힌트: 현재 브랜치의 끝이 리모트 브랜치보다 뒤에 있으므로 업데이트가
힌트: 거부되었습니다. 푸시하기 전에 ('git pull ...' 등 명령으로) 리모트
힌트: 변경 사항을 포함하십시오.
힌트: 자세한 정보는 'git push --help'의 "Note about fast-forwards' 부분을
힌트: 참고하십시오.

```

### Solution
```

(base) daeheehan@DAEHEEui-MacBookPro _posts % git push origin +main
오브젝트 나열하는 중: 11, 완료.
오브젝트 개수 세는 중: 100% (11/11), 완료.
Delta compression using up to 16 threads
오브젝트 압축하는 중: 100% (8/8), 완료.
오브젝트 쓰는 중: 100% (8/8), 788 bytes | 788.00 KiB/s, 완료.
Total 8 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), completed with 3 local objects.
To https://github.com/DAEHEE97/DAEHEE97.github.io.git
 + e975f44...f333de0 main -> main (forced update)

```

---
# 3주차

## Divide and Conquer 분할 정복


### 병합정렬


### 퀵정렬


### 선택 알고리즘 n개의 데이터 k번째 작은 수


### 최근접 쌍 찾기 closest pair
