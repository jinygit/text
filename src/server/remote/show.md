---
layout: home
title: "연동 및 원격 등록"
keyword: "연동 및 원격 등록"
breadcrumb:
- "server"
- "remote"
- "show"
---

# 상세한 원격저장소의 정보 출력하기
--- 
remote 명령어는 간략한 원격 저장소 정보만 출력합니다.  

<br>

## show 옵션
---
원격 저장소의 좀 더 상세한 정보를 확인하고 싶다면 `show` 옵션을 같이 사용합니다.  

```
$ git remote show 원격저장소별칭
```

<br>

## 실습하기
---
다음과 같이 remote show 명령어를 실행하면 상세한 정보를 출력합니다.

```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/jinygit/gitstudy05.git
  Push  URL: https://github.com/jinygit/gitstudy05.git
  HEAD branch: master
  Remote branch:
    master tracked
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

<br>