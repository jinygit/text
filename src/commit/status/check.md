---
layout: git
title: "깃 Untracked 파일 확인하기"
keyword: "status, 워킹디렉터리, Untracked"
description: "깃은 새로운 파일이 워킹디렉터리 저장소에 생성되면, 자동으로 감지됩니다. 또한 Untracked 파일의 추적여부를 결정해 주어야 합니다."
breadcrumb:
- "commit"
- "status"
- "check"
---

# 깃에서 새 파일 생성 확인
---
`워킹 디렉터리`에 새 파일이 `생성`되었습니다.  

<br>

## 파일감지
---
워킹 디렉터리에 새 파일이 추가되면 깃은 변화된 상태를 `자동으로 감지`합니다.  
이때 깃 상태를 확인할 수 있는 명령어가 `status`입니다.  

<br>

## status 명령
---
`status` 명령어를 입력하면 `메시지가 출력`되는 것을 볼 수 있습니다.  

☜ 명령을 입력합니다.
```bash
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git status
On branch master
No commits yet

Untracked files: 
  (use "git add <file>..." to include in what will be committed)
        index.htm ☜ 새로운 파일이 등록된 것을 확인
nothing added to commit but untracked files present (use "git add" to track)
```

깃의 상태 메시지를 자세히 살펴 봅니다.
메시지 중간에 `Untracked files`가 표시되는 것을 확인합니다.  

방금 생성한 새로운 파일이 지금 Untracked 상태라는 의미입니다. 그럼 Untracked란 무엇일까요?

<br>

## Untracked files
---
우리는 새롭게 생성된 파일을 status 명령으로 확인을 해보았습니다.  

`Untracked files` 메시지는 워킹 디렉터리에 새로운 파일이 `등록`되었다고 알려 주는 것입니다.  
깃 배시 터미널로 실행하면 `추적되지 않은 파일`은 `빨간색`으로 표시합니다.  

<br>

## 감지
---
깃은 워킹 디렉터리에 새 파일이 추가되면 상태를 `감지`하고 향후 이력을 추적할지 여부를 `결정`해 주어야 합니다.  

> Note: 모든 실습은 깃의 계정 및 환경 설정이 된 상태에서 진행합니다.  
혹시 앞의 내용을 읽지 않고 바로 커밋을 학습한다면 이전의 내용으로 이동하여 `계정`과 `환경을 설정` 하세요.  

<br>