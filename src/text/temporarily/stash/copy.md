---
layout: git
title: "스태시"
keyword: "스태시, stash"
---

## 스태시 복사
---
스태시는 브랜치 작업들을 임시로 저장할 때 사용합니다. 또 임시 저장된 작업을 스태시 명령 이전의 브랜치 상태로 되돌려 놓습니다. 스태시를 사용한 저장과 복원은 서로 다른 브랜치에도 가능합니다. 반드시 이전에 실행한 브랜치와 같은 브랜치에서 할 필요는 없습니다.  

앞에서 실습한 것처럼 다른 브랜치에서 스태시를 실행한 후 새로운 test 브랜치를 생성하여 스태시를 복원했습니다. 스태시 스택에 저장된 항목들은 어느 브랜치에서나 복원이 가능합니다. apply 옵션은 스택에 저장된 항목을 불러와 현재 브랜치로 복원합니다.  

```
$ git stash apply
```
 
스태시 복원은 pop, apply 명령어 2개를 제공합니다. 두 명령어에는 차이가 있습니다. 스태시의 pop 명령어는 스택 내용을 복원한 후 스택 목록에서 자동으로 삭제합니다. 즉, pop 명령어는 스택 내용을 워킹 디렉터리로 이동하는 것과 같습니다. 하지만 스태시 복원을 하고 난 후 스택 목록을 삭제하고 싶지 않을 때도 있습니다. 이때 apply 옵션을 사용합니다. 스택 목록을 읽은 후 자동으로 삭제하지 않기 때문에 반복적으로 스택에서 스태시 내용을 읽어 올 수 있습니다. apply 명령어는 스태시 내용을 워킹 디렉터리로 복사하는 것과 같습니다.  

apply 명령어를 실습하기 위해 현재의 임시 작업 내용을 다시 스태시로 저장합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (test)
$ git stash
Saved working directory and index state WIP on test: a43043e new feature start
```

현재 출력되는 스태시 목록은 test 브랜치에서 작업 중인 내용입니다. feature 브랜치로 이동한 후에도 스태시에 저장된 내용을 확인할 수 있습니다. stash 명령어로 임시 작업 내용들을 스택에 저장하면 브랜치 간 이동이 가능합니다. 기존 checkout 명령어를 사용하여 feature 브랜치로 이동합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (test)
$ git checkout feature
Switched to branch 'feature'
```

그리고 feature 브랜치에서 스태시 스택 목록을 확인합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash list
stash@{0}: WIP on test: a43043e new feature start ☜test에서 저장된 스태시
```

스태시의 저장 구조는 스택이며, 스택에 임시 작업 내용을 여러 개 저장할 수 있다고 했습니다. 그리고 작업 내용이 여러 개 저장되었을 때는 stash@{번호} 형태로 출력됩니다. 스택은 마지막에 저장된 작업을 가장 먼저 불러오는 구조입니다. apply 명령어는 pop 명령어와 달리 마지막 작업 내용이 아니라, 스택 목록의 중간 작업을 지정하여 적용할 수 있습니다. 이때는 다음과 같이 apply 명령어 뒤에 스태시 이름을 적어 주면 됩니다.  

```
$ git stash apply stash@{1}
```

앞의 예처럼 특정 스태시를 선택해서 현재 브랜치의 워킹 디렉터리로 복원할 수 있습니다. 특정 스택의 번호를 명시하지 않는다면 스택 특징에 따라 가장 최신 스태시로 복원합니다.  

스태시 번호를 이용해서 복원해 보겠습니다. 0번 스태시로 복원할 것입니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash apply stash@{0} ☜0번 스태시로 복원
On branch feature
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   stash.htm
no changes added to commit (use "git add" and/or "git commit -a")
```
 

선택한 스택을 읽어 와 현재 브랜치의 워킹 디렉터리로 복원했습니다. 다시 스태시 목록을 확인해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash list
stash@{0}: WIP on test: a43043e new feature start ☜스택 목록 남아 있음
```

스태시를 복원한 후에도 아직 스택 목록은 남아 있습니다. 이처럼 apply 명령어는 스택을 복원한 후에도 자동으로 삭제되지 않고 스택 목록에 남아 있습니다. 이러한 특징을 이용하여 여러 브랜치의 워킹 디렉터리로 스태시의 임시 작업 내용을 복사할 수 있습니다. 이는 스태시를 이용한 Ctrl+C와 Ctrl+V라고 생각하면 됩니다.

<br>