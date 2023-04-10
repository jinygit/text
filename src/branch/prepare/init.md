---
layout: home
title: "실습 준비"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
breadcrumb:
- "branch"
- "prepare"
- "init"
---


## 저장소 생성 및 초기화
---
브랜치 실습을 위한 실습환경을 구축합니다.

실습 메인폴더로 이동한 후에 새로운 실습폴더를 하나 생성합니다.
```
$ cd 메인폴더
$ mkdir gitstudy06
$ cd gitstudy06
infoh@DESKTOP MINGW64 /e/gitstudy06
```

실습폴더를 깃으로 초기화 합니다.
```
$ git init
Initialized empty Git repository in E:/gitstudy06/.git/
```

실습 터미널 환경은 `깃 배시`로 사용합니다. 여기서 초기화 명령어를 실행합니다. 
저장소가 초기화되면 다음과 같이 터미널 프롬프트 창에 현재` 브랜치 이름`이 같이 출력됩니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
```

현재 브랜치가 `master`라는 것을 확인할 수 있습니다.  
깃 배시는 리눅스 명령을 사용할 수 있고, 현재 브랜치의 작업 위치도 쉽게 알 수 있습니다.  

<br>