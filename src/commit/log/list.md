---
layout: home
title: "커밋 로그"
keyword: "커밋 로그"
breadcrumb:
- "commit"
- "log"
- "list"
---

# 간략 로그
---
커밋 메시지를 여러 줄 작성했다면 일반적인 로그 정보를 복잡하게 느낄 수 있습니다.  
로그 옵션 중에서 `--pretty=short`를 사용하면 로그를 출력할 때 첫 번째 줄의 커밋 메시지만 출력합니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git log --pretty=short ☜ 로그 확인
commit aa92947d350db27b604d1351930d4f809f96886e (HEAD -> master)
Author: hojin <infohojin@gmail.com>

commit aa1dd51a8883b2ea9a54209a00f434a2da01ee85
Author: hojin <infohojin@gmail.com>
    hello git world 추가

commit e2bce41380691b0a34aeab7db889a6c30fed8287
Author: hojin <infohojin@gmail.com>
    인덱스 페이지 레이아웃

```

특정 커밋의 상세 정보도 확인할 수 있습니다.  
특정 커밋의 상세 정보를 확인하고 싶다면 `show` 명령어를 사용합니다.  

```
$ git show 커밋ID
```

<br>
