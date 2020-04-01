---
layout: home
title: "수동으로 내려받기"
keyword: "수동으로 내려받기, fetch"
---

# 수동으로 내려받기
---
원격 저장소 내용을 내려받는 방법은 크게 두 가지입니다. pull(풀)과 fetch(페치)입니다. 이 두 방법의 차이는 병합을 자동 처리하는지 여부입니다. 병합은 8장에서 자세히 설명합니다. 이 장에서는 페치 병합 방법만 알고 넘어갑니다.  

<br>
<a name="1"></a>

## 자동 병합
---
풀은 원격 서버에서 현재 커밋보다 더 최신 커밋 정보가 있을 때 내려받습니다. 내려받은 커밋 정보는 임시 영역에 저장합니다. 스테이지 영역이 아닌 원격 저장소를 위한 전용 임시 브랜치가 따로 있습니다.  

내려받은 최신 커밋들을 현재 브랜치로 자동으로 병합 처리합니다. 여기서 병합은 원격 서버 파일과 로컬 파일을 하나로 합치는 과정입니다. 혼자서 개발하는 프로젝트는 pull 명령어만으로도 편리하게 사용할 수 있습니다.  

하지만 여러 개발자와 협업으로 코드를 작성할 때 pull 명령어를 사용한 자동 병합은 가끔씩 문제가 생깁니다. 여러 개발자와 협업하는 과정에서 pull 명령어가 자동으로 브랜치 병합을 하지 못하고 충돌이 발생하기도 합니다. 충돌은 8장 병합 부분에서 자세히 설명합니다.  

이처럼 pull 명령어로 자동 병합을 하지 못할 때는 페치 방식을 사용해야 합니다.  

<br>
<a name="2"></a>

## fetch: 가져오기
---
fetch(페치)는 원격 저장소에서 코드를 수동으로 내려받는 작업을 합니다. 페치는 원격 저장소에서 커밋된 코드를 임시 브랜치로 내려받습니다. 내려받은 후 현재 브랜치와 자동 병합하지 않습니다.  

```
$ git fetch 원격저장소URL
```
 
그럼 페치 동작을 실습해 봅시다. 먼저 실습 원본 저장소로 이동합니다.  

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ cd ../ gitstudy05 ☜ 폴더 이동

infoh@hojin MINGW64 /e/gitstudy05 (master)
$ code server.htm ☜ VS Code 실행
```

server.htm
```html
<h1>서버 실습입니다.</h1>
<h2>오늘도 좋은 하루 입니다.</h2>
<h2>가끔은 하늘을 보세요</h2>
```

수정된 파일을 스테이지 영역에 등록과 동시에 커밋합니다.  

```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git commit -am "look sky"
[master 668b5ef] look sky
 1 file changed, 1 insertion(+)
```

커밋된 수정 내용을 원격 저장소로 전송합니다.  

```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 369 bytes | 369.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/jinygit/gitstudy05.git
   6a947b8..668b5ef  master -> master
```

원본 저장소 변경과 원격 저장소를 갱신했습니다. 이제는 다시 복제된 로컬 저장소로 이동하여 갱신된 원격 저장소 내용을 페치해 보겠습니다.  

```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ cd ../ gitstudy05_clone

infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/jinygit/gitstudy05
   6a947b8..668b5ef  master     -> origin/master
```

원격 저장소의 커밋 내용을 페치한 후 커밋 로그를 확인합니다.  

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git log
commit 6a947b89517661cde95c9bec4c766302a763437e (HEAD -> master)
Author: hojinlee <infohojin@gmail.com>
Date:   Thu Dec 12 17:28:20 2019 +0900

    good day

commit 486458111de5ec909e43460ec8ebf945ba9e932c
Author: hojinlee <infohojin@gmail.com>
Date:   Thu Dec 12 17:16:37 2019 +0900

    first commit
```

pull 명령어와 달리 fetch 명령어를 실행한 후에는 커밋이 추가된 것을 확인할 수 없습니다. 페치는 원격 저장소의 커밋들만 가지고 왔을 뿐 로컬 저장소에서 어떤 작업도 하지 않습니다.  

>Note: 수동 병합인 페치 동작을 하면 새로운 master 브랜치를 하나 더 생성합니다. 서버/master 형태의 임시 브랜치입니다. 임시 브랜치에는 커밋을 할 수 없습니다.  

<br>
<a name="3"></a>

## merge 명령어로 수동 병합
---
페치는 데이터를 내려받기만 할 뿐 자동 병합하지 않습니다. 내려받은 커밋을 로컬 저장소에 적용하려면 병합 명령을 실행해야 하는데, merge 명령어를 사용합니다. 병합은 8장에서 자세히 설명하므로 여기서는 간단히 알아보겠습니다.  

merge 명령어는 다음과 같이 사용합니다.  

```
$ git merge 원격저장소별칭/브랜치이름
```
 
fetch 명령어로 내려받은 커밋을 로컬 저장소에 병합하겠습니다. 다음과 같이 merge 명령어를 입력합니다.  

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git merge origin/master
Updating 6a947b8..668b5ef
Fast-forward
 server.htm | 1 +
 1 file changed, 1 insertion(+) 
```

이전과 다른 메시지들을 출력했지만, 어쨌든 잘 병합되었습니다. 다시 로컬 저장소의 로그 기록을 확인합니다.  

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git log
commit 668b5efb139f47d28e77d6cb99863e3961a5db1d (HEAD -> master, origin/master, origin/HEAD)
Author: hojinlee <infohojin@gmail.com>
Date:   Thu Dec 12 17:32:36 2019 +0900

    look sky

commit 6a947b89517661cde95c9bec4c766302a763437e
Author: hojinlee <infohojin@gmail.com>
Date:   Thu Dec 12 17:28:20 2019 +0900

    good day

commit 486458111de5ec909e43460ec8ebf945ba9e932c
Author: hojinlee <infohojin@gmail.com>
Date:   Thu Dec 12 17:16:37 2019 +0900

    first commit 
```

`fetch` 명령어로 내려받은 커밋들이 추가된 것을 확인할 수 있습니다.  

<br><br>