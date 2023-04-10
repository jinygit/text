---
layout: home
title: "연동 및 원격 등록"
keyword: "연동 및 원격 등록"
breadcrumb:
- "server"
- "remote"
- "add"
---


# 원격 저장소에 연결
---
이제 원격 저장소와 연결해 보겠습니다.  

<br>

## 등록 명령옵션
---
원격 저장소와 연결하려면 `add `옵션을 사용합니다.  

```
$ git remote add 원격저장소별칭 원격저장소URL
```
 
원격 저장소를 추가할 때는 인자 값으로 원격 저장소 `별칭`과 원격 저장소의 `URL`을 같이 입력합니다.  
별칭은 앞에서도 이야기했듯이, 서버 주소가 길기 때문에 쉽게 작업하려고 사용하는 `별명`입니다.  

<br>

## 실습해보기

add 옵션을 이용하여 원격저장소를 등록해 봅니다.

```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git remote add origin https://github.com/jinygit/gitstudy05.git
```

원격저장소가 잘 등록 되었는지 목록을 확인해 봅니다.

```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git remote -v
origin  https://github.com/jinygit/gitstudy05.git (fetch)
origin  https://github.com/jinygit/gitstudy05.git (push)
```

<br>

## url 주소
---
원격 저장소가 연결되면 `fetch`와 `push` 두 주소를 출력합니다.  
push(푸시)는 서버로 전송하는 동작을 의미하고, fetch(페치)는 반대로 서버에서 가지고 오는 동작을 의미합니다.  

별칭은 `중복`하여 선택할 수 없습니다.  
