---
layout: home
title: "Git 교과서"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
breadcrumb:
- "hook"
---

## 기타 훅
---
기본적인 동작의 훅 이외에 몇 가지 추가적인 동작에 대해 설명합니다.

<br>

### pre-rebase
---
리베이스 동작 시 실행되는 스크립트입니다.

이미 원격 서버로 푸시된 커밋을 리베이스하는 것은 좋은 방법이 아닙니다. 만일 실수로 푸시된 커밋을 리베이스하려고 한다면 이를 감지하여 동작을 처리할 때 유용합니다.

반환값이 0이 아닌 경우 취소할 수 있습니다.

<br>

### post-rewrite
---
깃은 작성된 커밋의 메시지나 통합을 할 수 있는 기능이 있습니다. 

```
$ git commit --amend
$ git rebase
```

위와 같은 명령어를 사용하면 됩니다. post-rewrite는 커밋을 변경하고자 할 때 실행되는 스크립트입니다.

<br>

### post-checkout
---
브랜치 또는 개별 파일을 체크아웃 동작을 할 때 실행되는 스크립트입니다.

<br>

### post-merge
---
병합 동작이 완료된 후에 동작을 하는 스크립트입니다. 

<br>

### pre-push
---
푸시 명령을 실행하기 전 단계에서 동작을 하는 스크립트입니다. 푸시는 원격 저장소의 리모트 정보를 갱신한 후, 실제 데이터를 전송하기 전단계에 실행됩니다.

반환값을 통하여 푸시 동작을 취소할 수 있습니다.

<br>

### pre-auto-gc 
---
깃은 다른 동작을 실행하는 도중 가비지 컬렉션을 실행하는 경우가 있습니다.  
만일 깃이 카비지 컬렉션을 실행하고자 할 때, 이를 감지하여 실행할 수 있는 스크립트입니다.

이 스크립트를 통해 사용자가 깃의 가비지 동작을 알아챌 수 있습니다.  
또는 가비지 동작을 취소할 수도 있습니다.