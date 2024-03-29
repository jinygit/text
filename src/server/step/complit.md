---
layout: home
title: "순서"
keyword: "순서"
breadcrumb:
- "server"
- "step"
- "complit"
---

# 충돌 방지
---
깃이 최신 상태에서만 푸시를 허용하는 것은 `충돌`을 방지하기 위해서입니다.  

<br>

## pull 병합충돌
---
원격 저장소의 커밋을 내려받는 `pull` 작업은 내려받은 커밋들을 `현재 브랜치`로 `자동 병합`합니다.  
이때 커밋 내용이 `순차`적이지 않으면 `병합` 과정에서 `충돌`이 발생합니다.  

개발자 1과 개발자 2가 서로 다른 작업을 했다면 충돌이 없을 수도 있지만, 같은 영역을 동시에 수정했다면 개발자 2가 풀 작업을 할 때 무조건 충돌이 발생합니다.  
개발자 2는 충돌을 해결한 후 커밋하고 푸시해야 하는데, 이를 해결하기가 어렵습니다.  

따라서 깃은 이를 더 쉽게 해결할 수 있도록 푸시할 때 커밋의 `순차적 기록`을 확인합니다.  

<br>

## 원격저장소 확인하기
---
`push` 명령어를 사용할 때는 충돌을 최소화하기 위해 `미리 원격 저장소를 확인`합니다.  
새로운 커밋 갱신이 없는지 pull 명령어를 사용하여 지속적으로 확인하는 것이 좋습니다.  

최대한 충돌을 피할 수 있는 방법은 자신의 저장소와 원격 저장소의 상태를 자주 `최신으로 유지`하는 것입니다.  

권장 순서  
![권장 순서](../img/05-10.jpg)

풀(pull)과 푸시(push)를 자주 하여 충돌을 최소한으로 줄여 나가면서 작업을 유지합시다.  

<br>

## 소스트리
---
소스트리를 사용하면 푸시하기 전에 자신의 저장소와 어떤 차이점이 있는지 쉽게 확인할 수 있습니다.  
소스트리의 push 5-a.jpg 위에 조그마한 숫자가 표시됩니다. 숫자는 현재 로컬 저장소와 원격 저장소 간 커밋 차이점을 출력합니다.  

<br>

## Note: 인증 정보 캐시  
---
원격 저장소로 깃허브, 비트버킷 같은 호스팅 원격 저장소를 이용할 때는 아이디와 비밀번호가 있어야 접속할 수 있습니다.  
매번 아이디와 비밀번호를 입력하는 것은 귀찮습니다. 그래서 깃은 인증 정보 캐시(credential cache) 기능을 이용하여 아이디와 비밀번호를 임시적으로 보관할 수 있습니다.  

이 기능을 활성화하려면 다음과 같이 환경 설정이 필요합니다.  

```
$ git config --global credential.helper cache
```

<br>

## Note: 원격 저장소 원리  
---
깃을 원격 저장소에 연결하면 `.git/config` 파일 안에 리모트 연결에 대한 설정 정보가 자동으로 추가됩니다.  

```
[remote "origin"]
        url = https://github.com/jinygit/gitstudy05.git
        fetch = +refs/heads/*:refs/remotes/origin/* 
```

<br><br>