---
layout: home
title: "스테이지 등록 취소하기"
keyword: "스테이지, 추적, untracted, 취소"
description: "스테이지에 등록한 파일을 untracted 로 변경하여 취소를 합니다."
breadcrumb:
- "commit"
- "stage"
- "remove"
---

# 파일 등록 취소
---
이번에는 tracked 상태의 파일을 `untracked 상태`로 변경해 보겠습니다.  

<br>

## untracked
---
스테이지에 등록하는 것과 `반대 과정`입니다.  
등록 취소는 워킹 디렉터리와 스테이지 영역을 서로 왔다 갔다 할 수 있는 방법입니다.  

<br>

## 취소하기
---
unstage 상태로 변경하려면 `삭제(rm)`나 `리셋(reset)` 명령어를 사용합니다.  

스테이지 영역의 파일 등록 취소
![스테이지_영역의_파일_등록_취소](./img/04-10.jpg) 

<br>

## rm 명령 삭제
---
`rm 명령어`로 삭제해 보겠습니다.  
스테이지 영역에서만 등록된 파일을 삭제하려고 `--cached` 옵션을 함께 사용합니다.  

☜ 스테이지 삭제
```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git rm --cached index.htm 
rm 'index.htm'
```

스테이지의 캐시 목록에서 파일이 삭제됩니다.  
다시 status 명령어를 실행하여 확인합시다.  

☜ 상태 확인
```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git status 
On branch master
No commits yet
Untracked files: ☜ 추적하지 않음
  (use "git add <file>..." to include in what will be committed)
        index.htm ☜ 스테이지 삭제

nothing added to commit but untracked files present (use "git add" to track)
```

등록하기 이전의 untracked 상태로 변경되었습니다.  
다음 실습에 대비하여 다시 tracked 상태로 변경해 놓습니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git add index.htm ☜ 스테이지 다시등록
```

<br>

## reset으로 삭제
---
파일을 등록한 후 커밋하지 않고 바로 삭제하려면 `rm --cached` 명령어를 사용합니다.  
하지만 한 번이라도 `커밋`을 했다면 `reset 명령어`를 사용해야 합니다.   

예를 들어 커밋한 index.htm 파일을 `rm` 명령어로 삭제했다고 합시다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git rm --cached index.htm
rm 'index.htm'
```

삭제한 후 `status` 명령어를 실행하면 다음과 같이 이전과 `다른 결과`가 나옵니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
        deleted:    index.htm
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.htm ☜ 스테이지 삭제
```

파일이 untracked 상태가 되고, 스테이지 영역에서 파일이 삭제 처리됩니다.  
커밋 후 삭제는 파일이 삭제 또는 `변화된 것`으로 간주합니다.  

따라서 커밋된 파일은 리셋으로 삭제한 후 `정리`해 주어야 합니다.  

다음은 간단한 리셋 후 정리하는 명령어를 사용한 예입니다.  

☜ 리셋을 시도합니다.
```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git reset HEAD index.htm 
```

그리고 다시 status 명령어로 확인하면 정상적으로 커밋이 정리되었습니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git status ☜ 상태 확인
On branch master
nothing to commit, working tree clean
```

이처럼 터미널에서 unstage 상태 및 untracked 상태로 변경하는 것은 `복잡`합니다.  

<br>

## 소스트리
---
소스트리를 이용하면 스테이지 영역에 등록된 파일을 좀 더 쉽게 등록 취소할 수 있습니다.  
모두 스테이지에서 내리기와 선택 내용 스테이지에서 내리기를 사용하면 untracked 상태로 쉽게 변경할 수 있습니다.  

<br>