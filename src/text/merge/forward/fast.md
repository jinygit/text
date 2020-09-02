---
layout: home
title: "Fast-Forward"
keyword: "Fast-Forward"
breadcrumb:
- "text"
- "merge"
- "forward"
---

## Fast-Forward 병합 적용
---
커밋 작업은 분기된 feature 브랜치에서 모두 수행했습니다. 아직 master 브랜치에는 추가된 커밋이 없습니다.  

이러한 상태에서 두 브랜치를 병합합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git merge feature ☜ feature 브랜치를 병함
Updating f123d5c..7caf5f0
Fast-forward ☜ 병합 방식 표시 
 index.htm | 6 ++++++
 1 file changed, 6 insertions(+)
```

`feature` 브랜치의 커밋을 `master` 브랜치에 병합했습니다. 병합 메시지를 확인해 볼까요?  
메시지에 `Fast-Forward` 방식을 사용하여 병합했다고 출력됩니다.  

이 과정을 그림으로 나타내면 다음과 같습니다.  

병합한 후 커밋 구조  
![병합한 후 커밋 구조](./img/08-10.jpg)

이 그림처럼 feature 브랜치의 커밋들이 하나씩 master 브랜치로 병합합니다. master 브랜치에는 커밋이 하나도 없기 때문에 feature 브랜치가 master 브랜치로 이동한 것처럼 보입니다. 소스트리에서 병합 결과를 확인합니다.  

소스트리에서 병합 결과 확인  
![소스트리에서 병합 결과 확인](./img/08-11.jpg)

이처럼 병합한 후에는 master 브랜치의 마지막 커밋 위치와 feature 브랜치의 마지막 커밋 위치가 같습니다.  
동일한 HEAD 포인터를 가지게 됩니다.  

log 명령어로 커밋 기록을 확인합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git log -1
commit 7caf5f028ba013f1eb74e2f6c8cc400c02b0eb9c (HEAD -> master, feature)
Author: hojin <infohojin@gmail.com>
Date:   Thu May 16 16:54:30 2019 +0900
    add menu2
```

Fast-Forward 병합은 작업한 브랜치를 원본 브랜치에 병합할 때 작업한 브랜치의 시작 커밋을 원본 브랜치 이후의 커밋으로 가리킵니다.  
이는 단순히 커밋 위치를 최신으로 옮기는 것과 비슷합니다.  

Fast-Forward 병합을 잘했는지 결과를 확인해 봅시다. master 브랜치의 원본 파일에 feature 브랜치에서 수정한 내용이 반영되어 있으면 잘 병합한 것입니다.  

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
        </ul>
    </header>        
    <h1>hello GIT world!</h1>
</body>
</html>
```
 
master 브랜치의 index.htm 파일을 확인해 보니 잘 병합했네요.  
Fast-Forward 병합은 병합할 하나의 브랜치 파일을 기준 브랜치로 복사하여 수정된 파일을 원본에 그대로 적용한 것과 같습니다.  
즉, 원본에 추가된 내용이 없다는 가정하에 변경한 파일을 대체하는 것입니다.  

<br><br>