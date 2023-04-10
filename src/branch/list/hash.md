---
layout: home
title: "브랜치 확인"
keyword: "브랜치 확인"
breadcrumb:
- "branch"
- "list"
- "hash"
---

# 브랜치 해시
---
브랜치는 특정한 커밋의 해시 값(SHA1)을 가리킵니다.  

<br>

## 브랜치의 sha1
---
깃의 저수준 명령어인 `rev-parse`를 사용하면 현재 브랜치가 어떤 커밋 해시 값(`SHA1`)을 가리키는지 확인할 수 있습니다.  

```
$ git rev-parse 브랜치이름
```
 
<br>

## 커밋 관계
---
실습으로 브랜치와 커밋 간 관계를 확인해 보겠습니다.  
먼저 커밋 로그를 확인합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (feature)
$ git log
commit d84766c7f87b1d9d234050949c48681ba4e35da8 (HEAD -> feature, master, footer)
Author: hojin <infohojin@gmail.com>
Date:   Sat May 11 17:10:02 2019 +0900
    first
```

로그에서 커밋의 `d84766c7f87b1d9d234050949c48681ba4e35da8` 해시 값(SHA1)을 확인할 수 있습니다.  

<br>

## 브랜치 커밋
---
이번에는 footer 브랜치의 커밋 해시(SHA1)를 확인합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (feature)
$ git rev-parse feature
d84766c7f87b1d9d234050949c48681ba4e35da8
```

브랜치의 해시 값과 브랜치를 생성한 기준 커밋의 해시 값이 `동일`합니다.  
브랜치가 `커밋의 해시를 기준`으로 생성된다는 것을 다시 한 번 알 수 있습니다.  

<br>