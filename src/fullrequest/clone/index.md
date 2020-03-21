---
layout: home
title: "Git 교과서"
description: "버전 관리 시스템의 이해와 설치부터 커밋, 브랜치, 임시 처리, 병합, 복귀, 서브모듈, 태그까지
깃, 소스트리, 깃허브로 실습하며 기본기를 탄탄하게 다진다!"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# 복제(clone)
포크된 저장소의 코드를 자신의 로컬 컴퓨터로 복제합니다.

## 포크 저장소
포크는 본인 계정에 원격으로 복제합니다. 포크된 저장소는 원격 저장소이며 깃허브 서버에 존재하게 됩니다. 자신의 계정으로 복사했기 때문에 자동으로 새로운 저장소가 생성되고, 소유권도 본인에게 있습니다.

이제 포크된 저장소는 마음껏 수정할 수 있게 됩니다. 그리고 포크한 저장소를 자신의 로컬 저장소로 복제합니다.  

## 포크 내려받기
코드를 수정하기 위해 먼저 포크 저장소를 자신의 로컬 저장소로 복제해야 합니다. 깃허브 포크 저장소에 접속하여 URL을 확인합니다. 

![풀리퀘스트](./img/image010.png)  

포크된 저장소에서 `Clone or download`를 선택합니다. 포크된 저장소의 깃허브 주소를 알 수 있습니다.

깃 clone 명령어를 사용하여 자신의 로컬 저장소로 복제합니다.

```
infoh@hojin1 MINGW64 /e/jinygit
$ git clone https://github.com/hojin74/hello.git hello_fork
Cloning into 'hello_fork'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```

포크된 저장소를 로컬 컴퓨터로 clone 하였습니다.

![풀리퀘스트](./img/image011.png)  

저장소의 파일 목록을 확인해봅니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit_hello_fork (master)
$ ls
README.md
```

README.md
```md
# pull-request 인사를 하세요.
```

이제 코드를 수정할 수 있습니다.