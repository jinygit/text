---
layout: home
title: "status 명령으로 스테이지의 상태를 확인하기"
keyword: "status, 스테이지, 상태확인"
description: "status를 이용하여 스테이지의 상태를 확인합니다."
breadcrumb:
- "commit"
- "stage"
- "status"
---

# 파일의 추적 상태 확인
---
워킹 디렉터리에 있는 새로운 파일이 스테이지 영역에 `등록`되었습니다.  

<br>

## 스테이지 확인하기
---
콘솔창에서 status 명령어를 사용하여 등록 상태를 다시 한 번 확인해 보겠습니다.  

상태를 확인합니다.
```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git status 
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.htm ☜ 스테이지 등록, 새 파일 상태
```

이전 상태와 달리 `new file` 메시지가 출력됩니다.  
이는 스테이지 영역에 파일을 정상적으로 등록했다는 의미입니다.  

<br>

## 스테이지와 커밋관계
---
앞으로 좀 더 학습해야 하지만, 스테이지 영역에 `등록`되었다고 `커밋이 된 것은 아닙니다`.  

아직 커밋 명령어를 학습하지 않았습니다.  
등록은 커밋을 하기 전 `선행 작업`일 뿐입니다.  

<br>