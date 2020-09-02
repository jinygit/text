---
layout: home
title: "3-way 병합"
keyword: "3-way 병합"
breadcrumb:
- "text"
- "merge"
- "master"
---

## 마스터 변경
---
이번에는 브랜치 모양을 변경해 보겠습니다. master 브랜치에도 새로운 커밋을 추가하여 실습을 진행하겠습니다. 먼저 hotfix 브랜치에서 master 브랜치로 이동합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)
$ git checkout master
Switched to branch 'master'

infoh@DESKTOP MINGW64 /e/gitstudy08 (master) ☜ 원본 브랜치로 이동
```

그림 8-15] 원본 브랜치로 이동  
![원본 브랜치로 이동](./img/08-15.jpg)

hotfix 브랜치의 마지막 커밋은 7277f2d입니다. 그리고 master 브랜치의 마지막 커밋은 7caf5f0입니다. 시간적으로 좀 더 앞 단계인 master 브랜치에 새로운 커밋을 추가해 보겠습니다.  

master 브랜치의 index.htm 파일에 menu3을 추가하고 커밋합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
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
            <li>커밋</li>
        </ul>
    </header>        
    <h1>hello GIT world!</h1>
</body>
</html>
```
 
```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git commit -am "add menu3"
[master 49c98a1] add menu3
 1 file changed, 1 insertion(+)
```

다시 한 번 menu4를 추가하고 커밋합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
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
            <li>커밋</li>
            <li>브랜치</li>☜ 추가
        </ul>
    </header>        
    <h1>hello GIT world!</h1>
</body>
</html>
```
 
```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git commit -am "add menu4"
[master 8583edf] add menu4
 1 file changed, 1 insertion(+)
```

이제 메뉴가 4개입니다. master 브랜치에 추가 커밋이 발생하면 다음과 같이 브랜치는 7caf5f0을 기준으로 hotfix와 master 브랜치로 갈라집니다. 기준 커밋에서 서로 다른 브랜치의 커밋이 연결됩니다.  

그림 8-16] 기준 커밋에서 분기
![기준 커밋에서 분기](./img/08-16.jpg)


소스트리에서 master 브랜치의 그래프 모양을 확인해 보겠습니다. 이전 Fast-Forward 병합과는 달리 브랜치가 좀 더 확실하게 나뉘어 있습니다.  

그림 8-17] 소스트리에서 브랜치 그래프 확인  
![소스트리에서 브랜치 그래프 확인 ](./img/08-17.jpg)

<br>