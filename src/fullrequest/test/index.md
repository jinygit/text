---
layout: home
title: "Git 교과서"
description: "버전 관리 시스템의 이해와 설치부터 커밋, 브랜치, 임시 처리, 병합, 복귀, 서브모듈, 태그까지
깃, 소스트리, 깃허브로 실습하며 기본기를 탄탄하게 다진다!"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# 테스트
코드는 반드시 테스트후에 승인하는 것이 중요합니다. 요청받은 풀-리퀘스트를 테스트를 위해 새로운 저장소를 만들어 봅니다.

## 테스트 저장소
새로운 저장소를 생성하는 것은 기존의 코드와 문제를 발생하는 것을 미리 방지하기 위해서 복사본을 만들어 테스트하는 것입니다.

```
infoh@hojin1 MINGW64 /e/jinygit
$ git clone https://github.com/jinygit/hello.git hello-req1
Cloning into 'hello-req1'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```

테스트를 위해서 분리된 전용 저장소를 생성합니다. Hello-req1 이름으로 복제하였습니다.

```
$ cd hello-req1
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (master)
```

## 포크 저장소 연결
풀-리퀘스트를 받은 포크 저장소를 방금 생성한 복제된 로컬 저장소에 추가로 연결합니다. 
```
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (master)
$ git remote add hojin https://github.com/hojin74/hello.git
```

깃 remote -v로 원격 저장소의 목록을 확인해봅니다. 작업 로컬 저장소에는 원본 저장소와 포크 저장소 2개가 연결되어 있는 것을 확인할 수 있습니다.

```
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (master)
$ git remote -v
hojin   https://github.com/hojin74/hello.git (fetch)
hojin   https://github.com/hojin74/hello.git (push)
origin  https://github.com/jinygit/hello.git (fetch)
origin  https://github.com/jinygit/hello.git (push)
```

fetch 명령어를 사용하여 포크 저장소의 코드를 내려받습니다. 

```
$ git fetch 원격 저장소
```

페치 명령을 실행합니다. 
풀(pull) 대신 페치를 사용하는 것은 코드만 내려받고 원본 코드와는 자동 병합을 처리하지 않기 위해서입니다.

```
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (master)
$ git fetch hojin
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/hojin74/hello
 * [new branch]      master     -> hojin/master
```

페치는 원격 저장소로부터 데이터만 가지고 왔습니다. 
아직 새로운 내용이 반영되지 않았습니다. 

## 테스트 브랜치
포크 저장소의 코드를 테스트를 확인하기 위해서 새로운 브랜치를 만듭니다.

```
$ git checkout -b req1
Switched to a new branch 'req1'
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (req1)
```

방금 포크 저장소를 페치한 내용을 req1 브랜치와 병합합니다.

```
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (req1)
$ git merge hojin/master
Updating 4b595ec..4ce6391
Fast-forward
 README.md | 4 +++-
 1 file changed, 3 insertions(+), 1 deletion(-)
```

이처럼 페치로 내려받은 코드를 새로운 브랜치와 병합하여 사용하면 기존의 코드와 분리되어 충돌을 방지할 수 있습니다. 

## 코드 테스트
이제 브랜치에서 코드를 테스트해봅니다.

```
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (req1)
$ ls
README.md
```

목록과 반영하고자 하는 README.md 파일을 확인합니다.

```bash
infoh@hojin1 MINGW64 /e/jinygit/hello-req1 (req1)
$ cat README.md
# pull-request 인사를 하세요.
## 첫 번째 기여자 hojin입니다.
jinygit/hello를 포크하여 인사말을 풀-리퀘스트 해보세요.
```

젠킨스와 같은 외부 도구를 이용하여 코드 테스트를 사전에 실행해볼 수 있습니다.

## 브랜치 제거
병합하고자 하는 포크 저장소 코드가 이상이 없는지 확인합니다. 모든 테스트를 마쳤다면 기존에 생성한 브랜치는 삭제합니다.

```
$ git branch -D 브랜치
```

-D(대문자) 옵션을 이용하여 강제로 삭제합니다. 강제로 삭제하는 이유는 생성한 브랜치를 마스터에 병합하지 않기 때문에 -d(소문자) 옵션으로 삭제할 수 없습니다.

## 병합
모든 테스트 과정을 통과하였다면 포크 저장소의 풀-리퀘스트를 승낙합니다.

깃허브의 풀-리퀘스트 확인 화면에서 `Merge pull request`를 선택하면 자동으로 병합합니다. 
자동 병합은 깃허브의 원격 저장소에서 자동으로 수행되는 병합 작업입니다.

수동으로 풀-리퀘스트의 코드를 병합한 후에 메인 저장소로 푸시해도 됩니다. 
수동으로 병합하여 처리한 경우에는 풀-리퀘스트의 요청을 `open` -> `close` 상태로 전환해주도록 합니다.
