---
layout: git
title: "git 원격저장소를 삭제합니다."
keyword: "git, 원격저장소, 삭제"
description: "git 콘솔에서 등록된 원격저장소를 삭제하는 방법에 대해서 학습합니다. remote rm 옵션을 사용합니다."
breadcrumb:
- "server"
- "remote"
- "delete"
---

# 원격 서버 삭제
---
로컬 저장소는 복수의 원격 저장소와 연결할 수 있습니다.  
깃을 사용하다 보면 풀 리퀘스트(pull request) 테스트 등 목적으로 임시 등록된 원격 저장소들도 있습니다. 

<br>

## rm 옵션
---
등록된 원격 저장소는 `rm` 옵션으로 삭제할 수 있습니다.  

```
$ git remote rm 원격저장소별칭
```

<br>

## 실습하기
---
등록한 origin 저장소를 삭제하고, 목록을 다시 확인해 보겠습니다.  

* origin 저장소를 삭제합니다.
```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git remote rm origin
```

* 정상적으로 삭제가 되었는지 목록을 확인합니다.
```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git remote -v
```

이처럼 등록, 변경, 삭제하여 다수의 원격 저장소를 관리할 수 있습니다.  

<br>