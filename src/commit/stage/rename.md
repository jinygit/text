---
layout: git
title: "깃 파일이름 변경하여 재등록하기"
keyword: "스테이지, 추적, untracted, 이름변경"
description: "스테이지에 등록된 파일의 이릉을 변경하는 방법에 대해서 학습합니다."
breadcrumb:
- "commit"
- "stage"
- "rename"
---

# 등록된 파일 이름이 변경되었을 때
---
작업 도중 `파일 이름`도 변경할 수 있습니다.  
하지만 파일 이름을 변경했다고 별도로 깃에 통보할 필요는 없습니다.  
깃은 똑똑해서 변경된 파일 이름을 `자동`으로 알고 있습니다.  

<br>

## git mv 명령어
---
리눅스나 macOS에서는 mv 명령어로 파일 이름을 변경할 수 있습니다.  
깃에서도 파일 이름을 변경할 때 `mv` 명령어를 사용합니다.  

```
$ git mv 파일이름 새파일이름
```

다음과 같이 index.htm 파일의 이름을 변경하고 상태를 확인해 보면 깃에서 변경된 파일을 계속 추적하는 것을 알 수 있습니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git mv index,htm home.htm
$ git status
On branch master
No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   home.htm ☜ 파일 이름 변경
```

<br>

## git mv의 실제동작
---
굳이 git mv 명령어를 사용하지 않고, 운영 체제의 mv 명령어를 사용해도 됩니다.  
깃의 git mv 명령어를 여러 단계의 명령으로 풀면 다음과 같습니다.  

[예시]
```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ mv index.htm home.htm
$ git rm index.htm
$ git add home.htm
```

예에서 알 수 있듯이, 이름을 변경한다는 의미는 기존 파일을 삭제하고 새 파일을 `다시 스테이지 영역에 등록`하는 과정과 유사합니다.  
풀어 쓴 명령에서 이름을 변경한 후에는 `rm`과 `add` 명령어를 실행해야 한다는 사실을 잊지 마세요.  

<br>