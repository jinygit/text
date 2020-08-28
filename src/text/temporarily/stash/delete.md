---
layout: git
title: "스태시"
keyword: "스태시, stash"
---

## 스태시 삭제
---
스태시는 복원할 때 한 번 호출하면 자동으로 스택에서 삭제됩니다. 하지만 충돌이 발생하거나 apply 명령어로 워킹 디렉터리를 복구할 때는 스택에서 자동으로 삭제되지 않습니다. 이때는 별도 명령을 실행해야만 스태시 목록에서 삭제됩니다.  

```
$ git stash drop
```
 

이전 실습은 test 브랜치에서 저장한 임시 작업 내용을 apply 명령어를 사용하여 feature 브랜치로 복원했습니다. 그리고 스택 목록은 삭제되지 않고 남아 있습니다. 남아 있는 스택 목록을 삭제해 보겠습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash list
stash@{0}: WIP on test: a43043e new feature start

infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash drop
Dropped refs/stash@{0} (6f494132548e24cf44660a60739df21f78be587b)

```

참고로 스태시를 너무 많이 만들어 사용하는 것은 바람직하지 않습니다. 사용한 스태시는 그때그때 삭제하여 정리하는 것이 좋습니다.

<br>