---
layout: git
title: "스태시"
keyword: "스태시, stash"
---

## 스태시 복원으로 충돌
---
스태시를 복원할 때 워킹 디렉터리의 상태는 깨끗해야 합니다. 스택에 저장된 스태시 내용이 다시 워킹 디렉터리로 복구될 때, 수정된 작업 내용과 현재 워킹 디렉터리를 병합하기 때문입니다. 복구되는 브랜치의 워킹 디렉터리가 깨끗하지 않다면 병합 과정에서 충돌이 발생할 가능성이 많습니다.  

특히 스태시를 복원할 때 같은 파일에서 동일한 부분을 변경했다면 즉시 충돌이 발생합니다. 스태시를 복원할 때 충돌이 생기면 직접 문제를 해결해야 합니다. 복원하는 도중 충돌이 생기면 스태시는 스택에 저장된 내용을 자동으로 삭제하지 않습니다. 직접 충돌을 해결한 후 스태시 목록을 수동으로 삭제해야 합니다. 스태시 충돌이 예상된다면 스태시용 브랜치를 하나 생성해서 작업하는 것을 추천합니다.  

다음은 새로운 브랜치를 생성한 후 스태시를 적용하는 명령입니다. 스태시 스택에 저장된 내용으로 새로운 브랜치를 동시에 생성할 수 있습니다.  

```
$ git stash branch 브랜치이름
```

스태시로 이전 내용을 복원한 상태입니다. 아직 커밋을 수행하지 않았기 때문에 작업 중인 내용은 수정된 상태로 워킹 디렉터리에 남아 있습니다. 실습을 위해 현재의 임시 작업 내용을 다시 스태시해 보겠습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash
Saved working directory and index state WIP on feature: a43043e new feature start
```

현재 작업 내용을 다시 스태시하여 임시 저장했습니다. 스태시의 스택 목록을 확인합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash list
stash@{0}: WIP on feature: a43043e new feature start
```

스태시 내용이 하나 있는 것을 확인할 수 있습니다. 스태시 스택에 있는 내용을 새로운 test 브랜치를 생성해서 적용해 보겠습니다.  

stash 명령어와 branch 명령어를 같이 사용합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash branch test
Switched to a new branch 'test'
On branch test
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   stash.htm

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (9eb2b13f462d76dd8ffa30f6695c042932bece79)
```

새로운 브랜치 생성과 동시에 스태시의 임시 작업 내용을 복원했습니다. 다시 스태시 명령을 실행해서 스택 목록을 확인해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (test)
$ git stash list
```

정상적으로 스태시 복원이 적용되면 저장된 스택은 자동으로 삭제합니다.  

>Note: 스태시는 로컬 저장소에서 브랜치 간 저장과 스태시를 복원할 때 충돌이 발생하는 상황 외에, 원격 저장소와 연결하여 작업할 때 충돌이 발생하는 상황에도 사용할 수 있습니다. 예를 들어 원격 저장소에서 풀(pull) 작업을 하면 로컬 저장소는 갱신됩니다. 이때 스태시를 복구하면 원격 저장소 내용과 스태시 작업 내용이 충돌할 수 있습니다.

<br>