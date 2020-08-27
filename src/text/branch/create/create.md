---
layout: git
title: "브랜치 생성"
keyword: "브랜치 생성"
breadcrumb:
- "branch"
- "create"
- "create"
---

# 브랜치 생성
---
처음 생성되는 기본 master 브랜치 외의 브랜치는 사용자가 직접 branch 명령어를 입력하여 생성해야 합니다. 
브랜치를 생성한다는 것은 기본적으로 제공되는 master 브랜치 이외에 사용자가 직접 정의한 사용자 브랜치를 이야기하는 것입니다.  

브랜치는 깃에서 또 하나의 개발 분기점을 의미합니다. 새로운 개발 분기점이 필요할 때는 브랜치를 추가로 생성할 수 있습니다. 
브랜치 생성 개수에는 제한이 없습니다. 
필요한 만큼 여러 브랜치를 생성할 수 있으며, 각 브랜치를 구분하려면 브랜치별로 이름을 지정해야 합니다.  

브랜치를 생성할 때는 branch 명령어를 사용합니다.  

```
$ git branch 브랜치이름 커밋ID
``` 

branch 명령어 뒤에 브랜치 이름을 인자 값으로 추가합니다. 
브랜치 이름만 입력하면 현재 HEAD 포인터를 기준으로 새로운 브랜치를 생성합니다. 
직접 커밋 ID 인자 값을 지정하면, 지정한 커밋 ID를 기준으로 브랜치를 생성합니다.  

그림 6-3] 브랜치 생성  
![브랜치 생성](../img/06-3.jpg)

실습 환경을 만들어 봅시다. 저장소에 새로운 파일을 하나 생성한 후 저장합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ code branch.htm ☜ VS Code로 파일을 작성합니다
```

branch.htm
```html
<h1>브랜치 실습을 합니다.</h1>
```
 
```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git add branch.htm ☜ 추적 등록

infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git commit -m "first" ☜ 커밋 작성
[master (root-commit) cc66812] first
 1 file changed, 1 insertion(+)
 create mode 100644 branch.htm
```

코드를 저장하고 커밋을 하나 추가했습니다. 커밋이 있는 상태에서 새로운 브랜치를 생성합니다. 
마지막 커밋ID(100644)를 기준으로 브랜치를 생성 및 추가합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git branch footer

$ git branch
  footer
* master
```

브랜치를 생성할 때는 결과 메시지를 별도로 표시하지 않습니다. 
메시지가 없어도 정상적으로 브랜치가 생성된 것입니다.  

<br>