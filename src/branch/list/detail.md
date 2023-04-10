---
layout: home
title: "브랜치 확인"
keyword: "브랜치 확인"
breadcrumb:
- "branch"
- "list"
- "detail"
---

# 브랜치 세부 사항 확인
---
기본적인 branch 명령어는 간단한 브랜치 이름만 출력합니다.  
하지만 옵션을 사용하면 좀 더 상세한 브랜치 정보를 얻을 수 있습니다.  

<br>

## -verbose 옵션
---
branch 명령어 뒤에 -v 또는 -verbose 옵션을 함께 사용하면 브랜치 이름, 커밋 ID, 커밋 메시지를 같이 볼 수 있습니다.  

확인해 봅시다.  
```
infoh@DESKTOP MINGW64 /e/gitstudy06 (feature)
$ git branch -v
* feature d84766c first
  footer  d84766c first
  master  d84766c first
```

이전보다 좀 더 상세한 출력 결과를 얻을 수 있습니다.  
이처럼 branch 명령어는 다양한 옵션을 제공합니다.  

<br>

## -help 옵션
---
branch 명령어 뒤에 -help 옵션을 추가하면 자세한 사용법을 볼 수 있습니다.  

<br><br>