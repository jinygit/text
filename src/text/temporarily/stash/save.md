---
layout: home
title: "스태시"
keyword: "스태시, stash"
---

## 스태시의 임시 스택 영역에 작업 중인 코드 저장
---
우리는 현재 작업 중인 브랜치의 워킹 디렉터리를 정리하지 못한 상태입니다. 따라서 현재 브랜치에서 버그를 수정하기 위한 다른 브랜치로 체크아웃할 수 없습니다.  

다시 status 명령어를 실행하여 상태를 확인합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git status
On branch feature
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   stash.htm ☜ 수정 상태
no changes added to commit (use "git add" and/or "git commit -a")
```

브랜치를 이동할 수 없는 이유는 코드가 아직 수정 중인 상태이기 때문입니다. 이를 해결해야 다른 브랜치로 이동할 수 있습니다.  

스태시 명령어는 수정 중인 내역을 커밋하지 않고도 브랜치를 이동할 수 있게 워킹 디렉터리를 깨끗이 청소합니다. 따라서 커밋 대신 스태시 명령을 실행하면 됩니다. 스태시는 영구적인 커밋 기록 대신 현재 작업들을 임시 스택 영역에 저장합니다. 간략하게는 git stash 명령어만 사용합니다.  

```
$ git stash
```
 
또는 save 명령어를 추가하여 사용합니다. git stash save 명령어는 스태시 여러 개를 생성할 때 유용합니다.  

```
$ git stash save
```

스태시는 스택 구조로 여러 번 실행하여 저장할 수 있습니다. 스태시가 여러 개 있을 때 각각의 스태시를 구별할 수 있도록 메시지도 추가할 수 있습니다.  

```
$ git stash save "WIP: 메시지~~~"
```

브랜치에서 스태시 명령을 실행하면 작업 중인 내역들을 스택에 저장합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash
Saved working directory and index state WIP on feature: a43043e new feature start
```

다시 한 번 status 명령어를 실행하여 상태를 확인합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git status
On branch master
nothing to commit, working tree clean
```

워킹 디렉터리를 깨끗하게 정리했습니다. 그리고 워킹 디렉터리에서 작업 중인 임시 파일도 사라졌습니다.  

이제 다시 master 브랜치로 체크아웃해 봅니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git checkout master
Switched to branch 'master'

infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
```

정상적으로 master 브랜치로 체크아웃되었습니다.  

>Note: 스태시 기능을 사용하지 않는다면 작업 중인 내용을 강제로 커밋한 후 다시 리셋해서 복원해야 합니다. 이 작업은 복잡하므로 가능하면 스태시 기능을 사용하길 추천합니다.  

```
$ git commit -am “temp” ☜ 임시 커밋
$ // 다른 브랜치 작업들…
$ // 다시 현재의 브랜치로 돌아옴
$ git reset –soft HEAD^ ☜ 리셋 복원
```

스태시 작업을 할 때 스테이지 영역의 파일들을 제외할 수도 있습니다. --keep-index 옵션을 사용하면 스테이지 영역의 파일들을 제외하고 스태시를 만듭니다. 또 스태시는 등록된 파일들만 스태시로 생성합니다. 등록되지 않은 untracked 상태의 파일을 스태시로 생성하고 싶다면 --include-untracked 옵션을 같이 사용합니다.  

<br>