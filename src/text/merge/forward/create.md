---
layout: home
title: "Fast-Forward"
keyword: "Fast-Forward"
breadcrumb:
- "text"
- "merge"
- "forward"
---

## 브랜치 생성과 수정 작업
---
실습을 위해 새로운 feature 브랜치를 생성하겠습니다.  
그리고 feature 브랜치로 체크아웃합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git branch feature ☜ 브랜치 생성

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git checkout feature ☜ 브랜치 이동
Switched to branch 'feature'

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
```

브랜치를 생성할 때 분기 기준은 master의 `최종 커밋 포인터`입니다.  
포인터를 확인할 수 있는 `rev-parse` 명령어로 확인해 봅시다.  
첫 번째 커밋 f123d5c와 값이 동일합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git rev-parse feature
f123d5c9fd0c1f8a2f4ec86f63451a179371ae09
```

이 내용은 다음과 같이 나타낼 수 있습니다.

브랜치 생성  
![브랜치 생성](../img/08-3.jpg)


소스트리에서 생성된 브랜치를 확인할 수 있습니다.  

이 장에서는 깃 배시와 소스트리를 번갈아 가며 실습을 합니다.  
먼저 소스트리의 새 탭에서 Add 버튼을 클릭합니다.  
탐색을 눌러 앞에서 만든 gitstudy08 폴더를 찾아 선택한 후 추가를 누릅니다. 그러면 gitstudy08 저장소와 연결됩니다.  

생성한 feature 브랜치를 클릭하면 feature 브랜치와 master 브랜치의 시작 위치가 동일한 것을 확인할 수 있습니다.  

소스트리에서 브랜치 위치 확인  
![소스트리에서 브랜치 위치 확인](./img/08-4.jpg)


생성한 feature 브랜치 안에 있는 index.htm 파일을 수정하겠습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ code index.htm ☜ VS Code 실행
```

index.htm
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />    
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Page Title</title>
</head>
```
 
코드에 `<header></header>` 태그를 삽입하고 저장합니다. 기존 코드를 수정했기 때문에 파일 상태는 modified로 변경됩니다.  
다음과 같이 수정한 파일을 커밋합니다. `-a` 옵션과 같이 사용하면 스테이지 영역을 추가하면서 동시에 커밋을 할 수 있습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git commit -am "add header"
[feature 3f7799f] add header
 1 file changed, 2 insertions(+)
```

소스트리에서 커밋 로그를 확인해 보겠습니다.  
feature 브랜치가 master 브랜치보다 커밋이 하나 더 있는 것을 볼 수 있습니다.  

소스트리에서 커밋 위치 확인  
![소스트리에서 커밋 위치 확인](./img/08-6.jpg)

실습을 위해 수정과 커밋을 몇 번 더 합시다. 이번에는 `<header>` 코드 안에 `<ul><li>` 태그를 추가하여 두 번 커밋할 것입니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ code index.htm
```

index.htm
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />    
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Page Title</title>
</head>
<body>
    <header>
<ul>
        <li>깃소개</li>
</ul> 
    </header>
    <h1>hello GIT world!</h1>
</body>
</html>
```
 
```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git commit -am "add menu1"
[feature e762475] add menu1
 1 file changed, 3 insertions(+)
```

index.htm
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />    
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Page Title</title>
</head>
<body> 
    <header>
        <ul>
            <li>깃소개</li>
            <li>깃설치</li> 
        </ul>
</header> 
    <h1>hello GIT world!</h1>
</body>
</html>
```
 
```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git commit -am "add menu2"
[feature 7caf5f0] add menu2
 1 file changed, 1 insertion(+)
```

지금까지 과정을 그림으로 나타내면 다음과 같습니다.  

브랜치 생성 후 추가 커밋 진행 상태  
![브랜치 생성 후 추가 커밋 진행 상태 ](./img/08-7.jpg)

feature 브랜치에 추가된 커밋 로그를 확인해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git log
commit 7caf5f028ba013f1eb74e2f6c8cc400c02b0eb9c (HEAD -> feature)
Author: hojin <infohojin@gmail.com>
Date:   Thu May 16 16:54:30 2019 +0900
    add menu2

commit e76247541b07357220b042450aaf4a8aae037342
Author: hojin <infohojin@gmail.com>
Date:   Thu May 16 16:53:55 2019 +0900
    add menu1

commit 3f7799fb86b2b9abd980c26b1b2f33791e6708cf
Author: hojin <infohojin@gmail.com>
Date:   Thu May 16 16:45:42 2019 +0900
    add header

commit f123d5c9fd0c1f8a2f4ec86f63451a179371ae09 (master)
Author: hojin <infohojin@gmail.com>
Date:   Thu May 16 16:14:38 2019 +0900
    first
```

소스트리에서 브랜치의 커밋 로그를 확인해 보면, feature 브랜치가 master 브랜치에서 분리되어 header, menu1, menu2 커밋 작업을 세 번 수행한 것을 확인할 수 있습니다.  

feature 브랜치에 세 번 커밋됨  
![feature 브랜치에 세 번 커밋됨](./img/08-8.jpg)

우리는 브랜치를 만들어 feature 브랜치에 기능을 추가했습니다.  
하지만 소스트리에서 브랜치를 확인하면 브랜치 경로가 일직선으로 1개만 있습니다.  
서로 다른 브랜치이지만 순차적으로 커밋을 했기 때문에 일직선으로 보이는 것입니다.  
이러한 모양의 브랜치에서 병합 작업을 할 때는 Fast-Forward 방식의 알고리즘이 적용됩니다.  

<br>