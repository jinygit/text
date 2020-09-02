---
layout: home
title: "3-way 병합"
keyword: "3-way 병합"
breadcrumb:
- "text"
- "merge"
- "branch"
---

## 브랜치 생성과 수정 작업
---
직접 실습하며 3-way 병합을 익히겠습니다. 새로운 작업을 할 hotfix 브랜치를 생성하고, hotfix 브랜치로 체크아웃합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git checkout -b hotfix
Switched to a new branch 'hotfix'

infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)
```

현재 브랜치 위치는 hotfix입니다.  

그림 8-12] hotfix 브랜치 생성  
![hotfix 브랜치 생성](./img/08-12.jpg)

이번에는 소스 코드에 `<footer></footer>` 태그를 추가하고 내용을 적을 것입니다. 커밋 두 번으로 나누어 진행합니다. 먼저 `<footer>` 태그를 추가하고 저장합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)
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
            <li>깃설치</li>
        </ul>
    </header>        
    <h1>hello GIT world!</h1>

    <footer> ☜ 추가
    </footer>

</body>
</html>
```

수정한 파일은 Modified 상태가 됩니다. 수정한 파일을 다시 스테이지에 등록한 후 커밋합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)
$ git commit -am "add footer"
[hotfix c5df346] add footer
 1 file changed, 3 insertions(+)
```

다시 index.htm 파일에 `<footer>` 내용을 추가한 후 커밋합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)
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
            <li>깃설치</li>
        </ul>
    </header>        
    <h1>hello GIT world!</h1>
    <footer>
        copyright all right 2018 reserved by hojinlee ☜ 추가
    </footer>
</body>
</html>
```
 
```
infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)
$ git commit -am "add copyright"
[hotfix 7277f2d] add copyright
 1 file changed, 1 insertion(+)
```

이 과정을 그림으로 나타내면 다음과 같습니다.  

그림 8-13] hotfix 브랜치에서 파일 수정 및 커밋 로그  
![hotfix 브랜치에서 파일 수정 및 커밋 로그](./img/08-13.jpg)

소스트리에서 커밋 로그 기록을 확인하면 다음과 같습니다.  

그림 8-14] 소스트리에서 hotfix 브랜치의 커밋 로그 확인  
![소스트리에서 hotfix 브랜치의 커밋 로그 확인](./img/08-14.jpg)

hotfix 브랜치에 새로운 커밋이 2개 추가되었습니다. 지금까지 hotfix 브랜치에서 진행한 수정은 앞에서 실습한 Fast-Forward 병합과 유사합니다. Fast-Forward 병합에서는 생성한 브랜치에만 수정과 커밋을 했고, 원본 master 브랜치에서는 어떤 작업도 하지 않았습니다.  

<br>