---
layout: home
title: "깃의 파일 생성 감지"
keyword: "status, 워킹디렉터리"
description: "워킹디렉토리에 깃이 감지할 수 있는 새로운 파일을 하나 생성합니다. 그리고 상태를 확인해 보는 방법에 대해서 학습합니다."
breadcrumb:
- "commit"
- "status"
- "newfile"
---

# 새 파일 생성
---
실습을 위해 간단한 `HTML 파일`을 하나 작성합니다.  

<br>

## 실습 저장소 준비
---
커밋을 학습하기 위한 실습 저장소를 하나 생성합니다.  

☜ 새로운 실습 폴더를 생성합니다.
```bash
$ mdkir gitstudy04 
```

<br>

## 저장소 초기화
---
준비한 폴더를 깃 저장소로 `초기화`합니다.  

깃 초기화 명령을 입력합니다.

```bash
$ git init 
Initialized empty Git repository in E:/gitstudy04/.git/
```

> 여기서 실습한 깃 저장소는 깃허브를 통하여 확인할 수 있습니다. https://github.com/jinygit/gitstudy04

<br>

## html 파일 생성
---
실습을 위한 html 코드를 하나 작성합니다.  
에디터를 이용하여 코드를 작성하면 됩니다. 필자는 `VSCode`를 이용하겠습니다.

☜ VS Code를 사용해 파일을 작성합니다.
```
$ code index.htm 
```

콘솔에서 `code`명령을 입력하면, vscode를 실행할 수 있습니다.  

index.htm은 다음과 같이 작성합니다.  

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />    
    <meta name="viewport" content="width=device-width, initial-scale=1">
<title>Page Title</title>
</head>
<body>
    
</body>
</html>
```
 
작성한 예제 파일은 기본이 되는 HTML의 뼈대 페이지입니다.  

<br>

## 저장소와 파일 생성
---
파일 생성 과정을 그림으로 표현하면 다음과 같습니다.  

파일 생성 과정  
![파일 생성 과정](./img/04-3.png) 

이렇게 파일을 생성하면 `워킹 디렉터리`에 `index.htm` 이름으로 저장됩니다.  

모든 작업은 `워킹 디렉터리` 안에서 진행됩니다.  

<br>
