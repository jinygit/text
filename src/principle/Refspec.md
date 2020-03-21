---
layout: home
title: "Git 교과서"
description: "버전 관리 시스템의 이해와 설치부터 커밋, 브랜치, 임시 처리, 병합, 복귀, 서브모듈, 태그까지
깃, 소스트리, 깃허브로 실습하며 기본기를 탄탄하게 다진다!"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
## 19.12 Refspec
원격 저장소를 등록할 때 로컬 저장소의 refs 와 원격저장소의 refs 를 매핑합니다.

### 19.12.1 매핑
로컬 저장소에 원격저장소를 remote add 하게되면 매핑정보를 기록합니다. 패핑정보는 .git/config 파일에 기록됩니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ cat .git/config
[core]
        repositoryformatversion = 0
        filemode = false
        bare = false
        logallrefupdates = true
        symlinks = false
        ignorecase = true
[remote "origin"]
        url = https://github.com/jinygit/gitstudy19.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
        remote = origin
        merge = refs/heads/master
```

깃은 원격 저장소의 refs/heads 의 정보를 읽어와서 이를 로컬 저장소의 refs/remotes/origin에 복사하게 됩니다. 

Refspec 매핑 형식은 `<src>:<dst>` 형태의 한쌍으로 저장을 합니다. `<src>`는 원격 저장소를 말하며, `<dst>`는 로컬 저장소를 말합니다. 예제에서 +refs/heads/* : refs/remotes/origin/* 처럼 기록된 정보를 확인 할 수 있습니다.

`+`기호
매핑 주소 앞에 있는 + 기호가 있는 경우가 있습니다. 기본적으로 fast-forward 방식의 업로드만 허용합니다. 그 외에는 거절이 됩니다.

하지만 +기호를 추가하시면 거절을 하지 않고, 강제 덥어쓰기 형태로 다른 방식의 업데이트를 허용하는 것입니다.

`*` 기호
매핑 주소뒤에는 아스테리크(*) 기호를 확인할 수 있습니다. 아스테리크(*)기호는 모든 단어들 대체하는 의미를 가지고 있습니다. 이를 통하여 여러 브랜치의 데이터를 읽어 올 수 있습니다.

### 19.12.2 패치 설정
원격 저장소의 Refspec 패치 설정은 원격 저장소에서 브랜치의 데이터를 읽어오는 방법을 지정하는 것입니다. 단일/다중/네임스페이스등을 추가하여 설정을 변경할 수 있습니다.

단일패치
특정한 브랜치만을 지정할 수도 있습니다. 예를 들어 마스터(master) 브랜치만 허용할 때는 아스테리크 기호 대신에 브랜치명을 지정하시면 됩니다.
```
fetch = +refs/heads/master : refs/remotes/origin/master
```

다중패치
아스테리크(*)기호 대신에 직접 브랜치명을 지정하는 경우에는 한 개만 패치할 수 있습니다. 

패치 정보는 여러 개를 동시에 설정을 할 수 있습니다. 그러면 한꺼번에 여러 개여 브랜치 정보를 패치하여 가지고 오게 됩니다.
```
[remote "origin"]
       url = https://github.com/jinygit/gitstudy19.git
fetch = +refs/heads/master : refs/remotes/origin/master
fetch = +refs/heads/develop : refs/remotes/origin/develop
```
Glob 표현
브랜치를 refspec에 입력을 할 때에는 정확한 브랜치의 이름을 적어 주셔야 합니다. 다음과 같이 
```
fetch = +refs/heads/fix* : refs/remotes/origin/fix*
```
fix*와 같이 Glob 패턴의 형식은 사용을 할 수 없습니다.

네임스페이스
fix/* 와 같이 네임스페이스를 이용하여 작성을 하는 것은 가능합니다.
```
fetch = +refs/heads/네임스페이스/* : refs/remotes/origin/네임스페이스/*
```
### 19.12.2 푸시
매핑 정보를 활용하여 원격저장소에서 브랜치를 가지고 오는 다양한 방법에 대해서 알아 보았습니다. 이번에는 반대로 매핑 정보를 이용하여 푸시(push)를 할 수 있습니다.

```
$ git push origin master:refs/hads/네임스페이스/master
```

위의 푸시(push)명령은 로컬의 master를 원격저장소의 네임스페이스/master 로 전송을 합니다.

매핑정보를 이용하여 명령을 간단하게 변경할 수 있습니다. 

```
[remote "origin"]
       url = https://github.com/jinygit/gitstudy19.git
fetch = +refs/heads/master : refs/remotes/origin/master
fetch = +refs/heads/develop : refs/remotes/origin/develop
push = refs/heads/master:refs/heads/fix/master
```

push 매핑정보를 추가하면 별도의 refspec 정보를 입력하지 않아도 자동으로 푸시(push)를 할 수 있습니다.

```
$ git push origin
```

로컬브랜치의 master를 원격 저장소의 fix/master로 자동 푸시(push)하도록 하는 설정입니다.


### 19.12.3 refs 삭제
Respect을 이용하여 서버에 있는 refs 정보를 삭제할 수 있습니다. <src>:<dst> Refspec 형식에서 <src> 부분을 비우고 명령을 실행하면 됩니다.

```
$ git push origin :abcd
```

등록한 Refspec을 삭제합니다.