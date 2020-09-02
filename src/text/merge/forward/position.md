---
layout: home
title: "Fast-Forward"
keyword: "Fast-Forward"
breadcrumb:
- "text"
- "merge"
- "forward"
---

## 병합 위치
---
깃의 merge 명령어는 브랜치를 병합합니다.  
merge 명령어는 현재 브랜치를 기준으로 다른 브랜치의 모든 커밋을 병합합니다.  

```
$ git merge 브랜치이름
```
 
브랜치를 병합하려면 기준과 대상이 있어야 합니다. 기준은 체크아웃된 현재 브랜치입니다.  
따라서 병합하려면 먼저 기준이 되는 브랜치로 이동해야 합니다.  
우리는 master 브랜치에서 feature 브랜치로 분기하여 작업했습니다.  
작업한 feature 브랜치를 다시 master 브랜치로 병합할 것입니다.  
병합을 하려면 먼저 master 브랜치로 체크아웃해야 합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)
$ git checkout master ☜ 기준 브랜치로 이동
Switched to branch 'master'

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
```

병합을 할 수 있게 기준 브랜치(master 브랜치)로 이동했습니다.  

병합을 할 수 있게 기준 브랜치로 이동  
![병합을 할 수 있게 기준 브랜치로 이동](./img/08-9.jpg)

master 브랜치로 체크아웃한 상태에서 파일(코드)을 확인해 봅시다. feature 브랜치에서 작업한 내용이 사라졌습니다.  

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
    <h1>hello GIT world!</h1>
</body>
</html>

```

원본의 master 브랜치에서 작업한 내용만 출력됩니다.  

이처럼 브랜치는 기존 원본을 유지한 상태에서 서로 간섭하지 않고 feature 브랜치에서 코드를 수정할 수 있습니다.  

이제 feature 브랜치에서 작업한 내용을 병합해 보겠습니다.  

<br>