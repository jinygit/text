---
layout: home
title: "메시지가 없는 빈 커밋"
keyword: "메시지가 없는 빈 커밋"
breadcrumb:
- "commit"
---

# 메시지가 없는 빈 커밋
---
커밋을 할 때는 반드시 커밋 메시지를 같이 작성해야 합니다.  
하지만 의미가 없는 커밋이라 커밋 메시지를 생략하고 싶을 때도 있습니다. 이러한 특별한 상황에 대비하여 깃은 메시지가 없는 커밋 작성도 허용합니다.  

이를 간단히 `빈 커밋`이라고 합니다.  
빈 커밋 작성 방법은 지금까지 살펴본 메시지 작성 방법과 약간 다릅니다.  

<br>
<a name="1"></a>

## 세 번째 커밋
---
실습을 위해 index.htm 파일 내용을 좀 더 수정하여 세 번째 커밋을 하겠습니다.  
간략하게 `<title>~</title>` 사이의 내용을 JINYGIT으로 수정한 후 저장합니다.  

VS Code 실행
```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ code index.htm ☜ VS Code 실행
```

index.htm
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />    
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>JINYGIT</title>
</head>
<body>
    <h1>hello GIT world!</h1>
</body>
</html>
```
 
파일을 수정한 후에는 반드시 다음과 같이 다시 수정된 파일을 스테이지 영역에 `재등록`합니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git add index.htm ☜ 스테이지 등록
```

* --allow-empty-message 옵션

터미널에서 메시지가 없는 빈 커밋을 작성하려면 `--allow-empty-message` 옵션을 사용합니다.

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git commit --allow-empty-message -m "" ☜ 커밋 메시지를 작성하지 않음
[master 42250c6] ☜ 빈 커밋
 1 file changed, 1 insertion(+), 1 deletion(-)

```

메시지가 없는 빈 커밋이 정상적으로 실행된 것을 확인할 수 있습니다.  

<br>
<a name="2"></a>

## 소스트리에서 빈 커밋
---
소스트리에서는 메시지가 없는 빈 커밋을 하기가 더 쉽습니다.  
예를 들어 파일 상태 탭을 선택한 후 아래쪽의 커밋 메시지 입력란을 비워 두고 커밋을 누르면 됩니다.  
그러면 다음과 같은 확인 메시지가 표시됩니다. 확인을 누르세요.  
이렇게 경고문을 알리는 것은 커밋 작업이 반드시 메시지를 작성하는 것을 원칙으로 하고 있기 때문입니다.  

그림 4-24] 빈 커밋 알림창  
![빈 커밋 알림창](./img/04-24.jpg) 

<br>
<a name="3"></a>

## 4.7.3 빈 커밋 확인
---
빈 커밋 메시지를 확인해 봅시다. 터미널에서 `log` 명령어를 입력합니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git log ☜ 로그 확인
commit aa92947d350db27b604d1351930d4f809f96886e (HEAD -> master)
Author: hojin <infohojin@gmail.com> ☜ 빈 커밋
Date:   Sat Jan 5 20:09:48 2019 +0900

commit aa1dd51a8883b2ea9a54209a00f434a2da01ee85
Author: hojin <infohojin@gmail.com>
Date:   Sat Jan 5 19:31:46 2019 +0900
    hello git world 추가

commit e2bce41380691b0a34aeab7db889a6c30fed8287
Author: hojin <infohojin@gmail.com>
Date:   Sat Jan 5 18:24:50 2019 +0900
    인덱스 페이지 레이아웃

```

최신 커밋 로그를 보면 메시지 내용이 없는 것을 확인할 수 있습니다.  

소스트리에서도 로그를 확인해 보면 다음과 같이 추가된 로그가 없습니다.  

그림 4-25] 소스트리에서 빈 커밋 확인  
![소스트리에서 빈 커밋 확인](./img/04-25.jpg) 

이처럼 메시지가 없는 빈 커밋을 실행할 수 있습니다.

>Note: 메시지 수정
간혹 커밋 메시지를 입력할 때 오타가 발생할 수 있습니다. 이때는 방금 전에 작성한 커밋 메시지를 수정해야 할 것입니다.  
깃은 마지막 커밋을 수정할 수 있는 `--amend` 옵션을 제공합니다.  

```
$ git commit --amend
```

이 명령어를 실행하면 직전 커밋 메시지를 에디터 창에 표시합니다.  
내용을 수정하여 저장하면 변경된 커밋을 확인할 수 있습니다.  

<br><br>