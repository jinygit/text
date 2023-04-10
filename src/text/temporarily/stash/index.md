---
layout: home
title: "스태시"
keyword: "스태시, stash"
---

# 스태시
---
작업 브랜치를 변경하려면 워킹 디렉터리는 깨끗한(clean) 상태로 정리되어 있어야 합니다. 워킹 디렉터리에 작업 중인 내용이나 커밋되지 않은 변경 사항들이 남아 있으면 브랜치를 변경할 수 없습니다. 예를 들어 브랜치에서 코드를 수정하는 도중에 새로운 버그가 발견됩니다. 또는 고객의 긴급한 요청으로 코드를 추가해야 하는 경우가 발생합니다. 하지만 현재 작업 중인 코드 역시 수정이 끝난 것은 아닙니다.  

이러한 상황은 실제 개발 작업 과정에서 자주 발생합니다. 일부 커밋하지 않은 작업 내용이 남아 있다면 브랜치 간에 이동할 수 없습니다. 그럼 어떻게 현재 수정 작업을 멈추고, 다른 브랜치에 있는 코드를 수정할 수 있을까요? 이러한 상황에서는 스태시(stash) 기능을 사용할 수 있습니다. 스태시는 간단히 말해 ‘안전한 보관’입니다.  

그림 7-1] 스태시  
![스태시](./img/07-1.jpg)

깃은 완료되지 않은 작업(커밋되지 않은 변경 내용)이 남아 있을 때, 현재 작업을 임시로 저장할 수 있는 스태시 기능을 제공합니다. 스태시는 ‘현재 워킹 디렉터리 내역을 별도의 스택 영역에 잠시 보관하라’는 명령입니다. 스태시는 브랜치를 이동할 때 작업 중인 내용 때문에 워킹 디렉터리가 충돌하는 것을 방지하는 데 사용합니다.  

스태시 명령을 실행하면 현재 작업 중인 내용은 임시 저장되고, 수정 전 마지막 커밋 상태로 돌아갑니다. 즉, 이전 커밋 후 작업하지 않은 상태의 워킹 디렉터리가 됩니다.  

스태시를 하려면 stash 명령어를 실행합니다. 기본 명령어로 스태시를 실행하거나 옵션을 사용하여 추가 기능을 선택할 수 있습니다. -help 옵션을 같이 입력하면 다양한 명령어를 확인할 수 있습니다. 스태시는 로컬 저장소에서만 사용 가능합니다.  

스태시 실습을 위해 새로운 저장소를 생성하겠습니다.  

```
$ cd 실습폴더
$ mkdir gitstudy07 ☜ 새로운 실습 폴더를 생성합니다.
infoh@DESKTOP MINGW64 /e/gitstudy07
$ cd gitstudy07 ☜ 실습 폴더 이동

infoh@DESKTOP MINGW64 /e/gitstudy07
$ git init ☜ 저장소 초기화
Initialized empty Git repository in E:/ gitstudy07/.git/
```

실습을 위해 stash.htm 파일을 작성한 후 저장합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ code stash.htm ☜ VS Code 실행
```

stash.htm
```html
<h1>스태시를 실습합니다.</h1>
```
 
생성한 파일을 등록 및 커밋합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ git add stash.htm

infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ git commit -m "first"
[master (root-commit) e41773e] first
 1 file changed, 1 insertion(+)
 create mode 100644 stash.htm
```

새 파일을 생성하고 첫 커밋을 실행했습니다. 커밋하면 워킹 디렉터리는 다시 깨끗한 상태로 바뀝니다. status 명령어로 깃 상태를 확인합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ git status
On branch master
nothing to commit, working tree clean
```

<br>

+ [기존 작업 도중에 새로운 변경 요청](stash/work)
+ [새 코드 작성 중 기존 코드를 수정](stash/edit) 
+ [스태시의 임시 스택 영역에 작업 중인 코드 저장](stash/save) 
+ [임시 저장 영역의 스택 목록](stash/list) 
+ [임시 저장한 스태시 불러오기](stash/load) 
+ [스태시 복원으로 충돌](stash/conflict) 
+ [스태시 복사](stash/copy) 
+ [스태시 삭제](stash/delete) 
+ [소스트리에서 스태시 사용](stash/sourcetree) 

<br>