---
layout: git
title: "브랜치 확인"
keyword: "브랜치 확인"
---

# 브랜치 확인
---
눈치가 빠른 독자라면 앞 실습에서 이미 간단히 브랜치 목록을 확인하는 방법을 다루었음을 눈치챘을 것입니다. 이 절에서는 브랜치 세부 사항을 확인하는 방법을 알아보겠습니다.  

<br>
<a name="1"></a>

## 간단 브랜치 목록
---
깃 배시에서 브랜치 목록을 확인하는 방법은 간단합니다. branch 명령어만 입력하면 됩니다. branch 명령어는 단독으로도 실행할 수 있습니다.

```
$ git branch
```

현재 브랜치 목록을 확인해 볼까요? git branch 명령어를 실행하면 현재 모든 브랜치가 나열됩니다. 그리고 * 표시가 된 브랜치로 자동 이동합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (feature)
$ git branch
* feature
  footer
master
```

생성된 전체 브랜치 목록을 출력합니다. 브랜치 이름 앞에는 별표(*)가 붙은 것을 확인할 수 있습니다. 별표(*)는 현재 선택된 브랜치를 의미합니다. 앞에서 우리는 소스트리에서 feature 브랜치를 생성했습니다. 그리고 소스트리 목록에서 ○ 마크가 이동된 것을 확인했습니다. 깃 배시에서는 `○` 마크 대신 별표(*)로 표시됩니다.  

<br>
<a name="2"></a> 

## 브랜치 해시
---
브랜치는 특정한 커밋의 해시 값(SHA1)을 가리킵니다. 깃의 저수준 명령어인 rev-parse를 사용하면 현재 브랜치가 어떤 커밋 해시 값(SHA1)을 가리키는지 확인할 수 있습니다.  

```
$ git rev-parse 브랜치이름
```
 
실습으로 브랜치와 커밋 간 관계를 확인해 보겠습니다. 먼저 커밋 로그를 확인합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (feature)
$ git log
commit d84766c7f87b1d9d234050949c48681ba4e35da8 (HEAD -> feature, master, footer)
Author: hojin <infohojin@gmail.com>
Date:   Sat May 11 17:10:02 2019 +0900
    first
```

로그에서 커밋의 d84766c7f87b1d9d234050949c48681ba4e35da8 해시 값(SHA1)을 확인할 수 있습니다.  
이번에는 footer 브랜치의 커밋 해시(SHA1)를 확인합시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (feature)
$ git rev-parse feature
d84766c7f87b1d9d234050949c48681ba4e35da8
```

브랜치의 해시 값과 브랜치를 생성한 기준 커밋의 해시 값이 동일합니다. 브랜치가 커밋의 해시를 기준으로 생성된다는 것을 다시 한 번 알 수 있습니다.  

<br>
<a name="3"></a>

## 브랜치 세부 사항 확인
---
기본적인 branch 명령어는 간단한 브랜치 이름만 출력합니다. 하지만 옵션을 사용하면 좀 더 상세한 브랜치 정보를 얻을 수 있습니다.  

branch 명령어 뒤에 -v 또는 -verbose 옵션을 함께 사용하면 브랜치 이름, 커밋 ID, 커밋 메시지를 같이 볼 수 있습니다. 확인해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (feature)
$ git branch -v
* feature d84766c first
  footer  d84766c first
  master  d84766c first
```

이전보다 좀 더 상세한 출력 결과를 얻을 수 있습니다. 이처럼 branch 명령어는 다양한 옵션을 제공합니다. branch 명령어 뒤에 -help 옵션을 추가하면 자세한 사용법을 볼 수 있습니다.  

<br><br>