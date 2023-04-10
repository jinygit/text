---
layout: home
title: "커밋 로그"
keyword: "커밋 로그"
breadcrumb:
- "commit"
- "log"
- "file"
---

# 특정 파일의 로그
---
전체 커밋과 달리 특정 파일의 로그 기록만 볼 수도 있습니다.  
이때는 log 명령어 뒤에 파일 이름을 적어 주면 됩니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git log index.htm ☜ 파일의 로그 확인
commit aa92947d350db27b604d1351930d4f809f96886e (HEAD -> master)
Author: hojin <infohojin@gmail.com>
Date:   Sat Jan 5 20:09:48 2019 +0900
```

log 명령어의 옵션은 매우 다양합니다. 실습해 나가면서 다양한 옵션을 사용해 볼 것입니다.  
소스트리를 이용하면 log 명령어와 복잡한 옵션을 사용하지 않아도 쉽게 로그 흐름을 파악할 수 있는 장점이 있습니다.  

>Note: log 명령어의 여러 옵션
* -p 옵션: diff 기능(수정한 라인 비교)을 같이 포함하여 출력할 수 있습니다.
* --stat 옵션: 히스토리를 출력합니다.
* --pretty=oneline 옵션: 각 커밋을 한 줄로 표시합니다.

<br><br>