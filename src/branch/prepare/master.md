---
layout: home
title: "실습 준비"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
breadcrumb:
- "branch"
- "prepare"
- "master"
---

# 기본 브랜치
---
모든 커밋과 이력은 `브랜치`에 기록됩니다.  

<br>

## master 브랜치
---
깃은 최소한 브랜치가 1개 이상 필요합니다. 따라서 저장소를 처음 초기화하면 master 브랜치 하나가 자동으로 생성됩니다.  
첫 번째 커밋은 master 브랜치에서 시작합니다.  

<br>

## status 명령으로 확인
---
초기화한 후에 status 명령어를 실행해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git status 
On branch master ☜ 브랜치 작업 위치
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```

status 명령어의 출력 결과 메시지에서 `On branch master`를 확인할 수 있습니다.  
깃에서는 항상 `현재 작업하는 브랜치 위치`를 확인하는 것이 중요합니다.  

<br>

## branch 목록으로 확인
---
`branch` 명령어로 현재 브랜치를 확인할 수 있습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git branch
* master
```

branch 명령어는 생성된 모든 브랜치를 출력합니다. 앞 코드에서는 master라는 이름의 브랜치가 하나 출력되었습니다.  

<br>

## 기본 브랜치 이름
---
깃에서 `기본적`으로 선택되는 브랜치는 `master`입니다.  
하지만 꼭 기본값인 master 이름을 그대로 사용할 필요는 없습니다.  
통상적으로 깃이 master 브랜치를 `자동`으로 생성하기 때문에 이를 그대로 많이 사용할 뿐입니다.  

<br>