---
layout: home
title: "브랜치 이동"
keyword: "브랜치 이동"
breadcrumb:
- "branch"
- "checkout"
- "clean"
---

# 워킹 디렉터리 정리
---
체크아웃을 사용하여 브랜치를 이동할 때는 주의 사항이 있습니다.  
현재 작업하고 있는 워킹 디렉터리를 정리하고 넘어가야 합니다.  

<br>

## 워킹디렉토리 변환
---
브랜치 동작 원리에서 브랜치가 변경되면 워킹 디렉터리도 같이 `변환`된다고 했습니다.  
따라서 워킹 디렉터리 안에서 작성하던 내용이 있고, 커밋을 하지 않았다면 체크아웃할 때 `경고`가 발생합니다.  

그럼 master 브랜치에서 코드를 수정해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
$ git checkout master
Switched to branch 'master'

infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ code branch.htm
```

branch.htm
```html
<h1>브랜치 실습을 합니다.</h1>
<h2>마스터 워킹 디렉터리 작업 중</h2>
```
 
저장은 하지만 커밋은 하지 않습니다. 
status 명령어로 확인해 볼까요?

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   branch.htm ☜ 워킹 디렉터리 수정 상태
no changes added to commit (use "git add" and/or "git commit -a")
```

<br>

## 정리하지 않은 워킹디렉토리에서 브랜치 변경
---
현재의 상태에서 브랜치를 변경해 봅시다.

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git checkout footer
Switched to branch 'footer'
M       branch.htm ☜ 워킹 디렉터리 수정 상태
```

브랜치를 체크아웃하여 새로운 메시지가 하나 더 추가되었습니다.  
branch.htm 파일이 `수정된 상태`라는 의미입니다.  

<br>

## 이동제한
---
워킹 디렉터리에서 작업하다 커밋하지 않고 남겨 둔 상태에서 다른 브랜치로 체크아웃하면 이처럼 브랜치 이동이 제한됩니다.  
깃은 향후 충돌을 방지하려고 워킹 디렉터리에 작업이 남아 있다면 경고 메시지를 보여 주고 브랜치를 변경할 수 없게 제한합니다.  

footer 브랜치는 master 브랜치를 기준으로 생성한 후 별도로 추가 작업을 하지 않았기 때문에 브랜치 생성 당시 master의 `dcdb1c1 커밋`을 가리킵니다.  
아직 브랜치 2개가 가리키는 커밋 위치는 같습니다.  

브랜치 간에 정상적으로 이동하려면 남아 있는 작업들을 `정리`해 주어야 합니다.  
이전으로 돌아가 수정된 내용을 커밋합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git checkout - ☜ master로 이동
Switched to branch 'master'
M       branch.htm

infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git commit -am "master working..." ☜ 커밋, 워킹 디렉터리 정리
[master 9ca05fb] master working...
 1 file changed, 2 insertions(+), 1 deletion(-)

infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
$ git checkout footer
Switched to branch 'footer'
```

작업된 워킹 디렉터리를 커밋하지 않고 브랜치를 변경할 때는 `스태시` 기능을 이용하면 좋습니다.   

<br>