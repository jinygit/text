---
layout: home
title: "자동으로 내려받기"
keyword: "자동으로 내려받기"
---

# pull 실습하기
---
pull 동작을 실습해 보도록 합니다.

<br>

## 실습준비
---
실습을 위해 `원본` 로컬 저장소로 이동합니다.  

```
infoh@gitstudy MINGW64 /e/gitstudy05_clone (master)
$ cd ../ gitstudy05
```

<br>

## 원본 저장소 수정
---
원본 저장소를 정상적으로 pull을 해오는 확인을 하기 위해서 내용을 수정해 봅니다.  

수정을 위해서 vscode를 실행합니다.  
```
infoh@gitstudy MINGW64 /e/gitstudy05 (master)
$ code server.htm
```

내용을 수정합니다.

server.htm
```html
<h1>서버 실습입니다.</h1>
<h2>오늘도 좋은 하루입니다.</h2>
```

수정한 server.htm 파일을 스테이지에 등록하고 `커밋`을 합니다.  

스테이지 등록
```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git add server.htm
```

커밋명령 실행
```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git commit -m "good day"
[master 6a947b8] good day
 1 file changed, 2 insertions(+)
 create mode 100644 server.htm
```

이제 커밋한 내용을 다시 원격 저장소(서버)로 업로드합니다.
push 명령을 실행합니다.  
```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git push origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 341 bytes | 341.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/jinygit/gitstudy05.git
   4864581..6a947b8  master -> master
```

<br>

## 원본 저장소의 커밋을 pull 하기
---
방금 작성한 코드와 커밋으로 원격 저장소를 `갱신`했습니다.  
갱신된 원격 저장소의 커밋을 복제한 저장소에도 `동기화`합시다.  

<br>

### pull 명령을 수행하기전 상태확인
복제된 저장소로 이동합니다.  
```
$ cd ../ gitstudy05_clone/
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
```

복제된 저장소에서 커밋 `로그`를 확인해 보겠습니다.  

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git log
commit 486458111de5ec909e43460ec8ebf945ba9e932c (HEAD -> master, origin/master, origin/HEAD)
Author: hojinlee <infohojin@gmail.com>
Date:   Thu Dec 12 17:16:37 2019 +0900

    first commit
```

복제된 저장소에는 커밋 `하나`만 있습니다. 

<br>

### pull로 동기화 하기
이번에는 원격 저장소에서 갱신된 `새 커밋 정보`를 가지고 옵니다.  

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git pull
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/jinygit/gitstudy05
   4864581..6a947b8  master     -> origin/master
Updating 4864581..6a947b8
Fast-forward
 server.htm | 2 ++
 1 file changed, 2 insertions(+)
 create mode 100644 server.htm
```

pull 명령어는 원격 저장소에 갱신된 커밋을 로컬 저장소의 `커밋` 정보와 `비교`하여 `갱신`합니다.  

<br>

### log로 커밋 기록 확인하기
원격 저장소에서 복제된 저장소를 동기화했습니다.  
이제 다시 복제된 저장소에서 `log` 명령어를 실행합니다.  

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git log

commit 6a947b89517661cde95c9bec4c766302a763437e (HEAD -> master, origin/master, origin/HEAD)
Author: hojinlee infohojin@gmail.com ☜ 2번째 커밋 정보를 내려받았습습니다
Date:   Thu Dec 12 17:28:20 2019 +0900

    good day

commit 486458111de5ec909e43460ec8ebf945ba9e932c
Author: hojinlee <infohojin@gmail.com>
Date:   Thu Dec 12 17:16:37 2019 +0900

    first commit
```

복제된 저장소에 새로 추가된 커밋을 확인할 수 있습니다.  

이처럼 pull은 원격 저장소와 로컬 저장소 간 커밋을 반영할 수 있습니다.  

<br><br>
