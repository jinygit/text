---
layout: git
title: "스태시"
keyword: "스태시, stash"
---

## 기존 작업 도중에 새로운 변경 요청
---
개발자는 다양한 상황과 마주칩니다. 대표적으로 수정 작업을 하는 도중에 또 다른 수정 요청이 있는 경우입니다. 이때 현재 작업은 잠시 멈추고, 또 다른 요청을 반영하려면 새로운 브랜치가 필요합니다.  

* 상황 1  
실습을 위해 이야기한 상황과 유사한 작업 환경을 만들어 보겠습니다. 새로운 작업을 할 수 있게 브랜치를 하나 생성합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ git checkout -b feature ☜ 브랜치 수정과 체크아웃을 동시에 처리
```

생성된 feature 브랜치에서 stash.htm 파일을 수정하고, 저장한 후 커밋합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ code stash.htm ☜ 새로운 코드를 수정작성합니다.
```

stash.htm
```html
<h1>스태시를 실습합니다.</h1>
<h2>새로운 기능을 시작합니다.</h2>
```
 
```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git commit -am "new feature start"
[feature a43043e] new feature start
 1 file changed, 2 insertions(+), 1 deletion(-)
```

수정 작업은 워킹 디렉터리에서 이루어집니다. 파일을 한 번 더 수정해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ code stash.htm
```

stash.htm
```html
<h1>스태시를 실습합니다.</h1>
<h2>새로운 기능을 시작합니다.</h2>
새로운 기능이 너무 복잡하네요. 시간이 많이 걸릴 것 같습니다.
```
 
파일을 수정한 후에는 커밋하지 않고 저장만 합니다. 저장한 후에는 status 명령어를 입력하여 상태를 확인합니다.  

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

status 상태 메시지에 코드가 수정되었다고 표시합니다. 아직은 원하는 모든 작업을 마무리하지 않은 상태입니다.  

<br>