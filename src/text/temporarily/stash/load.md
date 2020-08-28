---
layout: git
title: "스태시"
keyword: "스태시, stash"
---

## 임시 저장한 스태시 불러오기
---
스태시를 사용하는 목적은 현재 워킹 디렉터리를 커밋하지 않고 임시로 저장하기 위해서입니다. 임시 저장된 내용은 다른 수정 작업을 완료한 후에 다시 불러와 사용할 수 있습니다. 앞에서 임시 저장한 스태시를 불러와 실습을 계속 진행하겠습니다. 먼저 master 브랜치의 파일 버그를 수정한 후 커밋하겠습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ code stash.htm
```
 
stash.htm
```html
<h1>stash를 실습합니다.</h1>
```
 
한글 `스태시`를 영문 `stash`로 변경했습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ git commit -am "bug fix master"
[master 535d22c] bug fix master
 1 file changed, 1 insertion(+), 1 deletion(-)
```

버그를 수정했습니다. 다시 원래 브랜치(feature)로 이동합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (master)
$ git checkout feature
Switched to branch 'feature'
```

버그를 수정한 후 다시 원래의 작업 브랜치로 돌아왔습니다. 이전에 수정한 내역들이 남아 있지 않습니다. 스태시에 임시 저장한 작업 내용들을 읽어 다시 적용할 수 있습니다. 스태시 명령어 뒤에 pop 옵션을 추가합니다.  

```
$ git stash pop
```

스태시는 저장 공간이 스택 구조라고 했습니다. 따라서 스택에서 저장된 작업 내용을 읽어 올 때는 제일 마지막에 저장된 내용을 읽어 옵니다. 이러한 데이터의 순차적 특징은 스택의 원리 때문입니다.  

그럼 스태시에서 임시 저장된 작업 내용을 읽어 다시 적용합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash pop
On branch feature
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   stash.htm
no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (2a9eb4f25e601230f9e5d9feeca72facdf96cd8c)

```

스태시의 스택에 저장된 작업 내용이 다시 적용되었습니다. 스태시는 스택에서 내용을 읽어 올 때 현재 브랜치의 워킹 디렉터리와 자동으로 병합합니다. 자동 병합이 성공하면 읽어 온 내용을 스택에서 제거합니다.  

스태시에서 임시 저장된 작업 내용을 복원한 후 다시 스태시 목록을 확인합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git stash list

```

스태시 스택 목록에 내용이 없습니다. pop 옵션을 사용하면 스태시 저장 스택에서 항목을 가져오는 동시에 저장된 항목을 삭제하기 때문입니다.  

>Note: 스태시와 스테이지 영역
스태시는 스택에 저장할 때 워킹 디렉터리와 스테이지 영역의 파일까지 모두 보관합니다. 스태시로 복원할 때는 워킹 디렉터리만 되돌려 놓습니다. 스테이지에 등록된 스테이지 상태까지 복구하길 원한다면 --index 옵션을 사용해야 합니다.
```
$ git stash apply --index
```

<br>