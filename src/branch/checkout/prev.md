---
layout: git
title: "브랜치 이동"
keyword: "브랜치 이동"
breadcrumb:
- "branch"
- "checkout"
- "prev"
---

# 이전 브랜치
---
브랜치를 이동하려면 브랜치 `이름`을 적어 주어야 합니다.  


<br>

## 이전 브랜치
---
하지만 새로운 브랜치가 아닌 이전 브랜치로 좀 더 편하게 이동할 수 있는 방법이 있습니다.  
대시(-)를 사용하는 방법입니다. 리눅스에서 대시(-) 기호는 이전 디렉터리를 의미합니다.  
이 대시를 사용하여 쉽게 이전 브랜치로 이동할 수 있습니다.

```
$ git checkout -
```

<br>

## 실습 목록 확인하기
---
깃 배시에서 git branch -v 명령어를 다시 실행하면 master 브랜치로 `변경된 것`을 확인할 수 있습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git branch -v
  feature d84766c first
  footer d84766c first
* master d84766c first
```

<br>

## 이전 돌아가기
---
master 브랜치에서 이전 footer 브랜치로 돌아갑시다.

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git checkout -
Switched to branch 'footer'
infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)

``` 

이전 브랜치인 footer 브랜치로 되돌아간 것을 확인할 수 있습니다.  

<br>