---
layout: home
title: "워킹 디렉터리 파일 상태 추적"
keyword: "상태추적, 깃 활용, git, 깃 사용법, 깃허브, 소스트리, 깃교과서"
description: "깃 이력관리를 위한 상태추적에 대해서 알아봅니다. tracted 와 untracted의 개념과 깃의 동작원리에 대해서 학습해 보도록 합니다."
breadcrumb:
- "text"
- "concept"
- "working"
---

## 파일의 상태 추적
---
워킹 디렉터리안에 있는 파일들을 깃으로 관리받기 위해서는 상태 추적을 등록해야 합니다.  

`VCS`는 파일의 수많은 파일들의 상태를 관리하여 기록해야 하기 때문에 시스템에 많은 부하를 줍니다. 
하지만 깃이 다른 `VCS`보다 뛰어난 것은 `지정한 파일들만을 추적`하는 관리 시스템이기 때문입니다. 

깃은 워킹 디렉터리에 있는 파일들을 `추적됨`과 `추적되지 않음` 상태로 구분합니다. 
깃의 추적(tracked) 개념을 알아봅시다.  

<br>

## untracked 상태  
---
우리가 실제 `작업 중인 파일`은 모두 워킹 디렉터리 안에 존재 합니다.  

워킹 디렉터리는 작업 중인 소스 코드 파일을 모두 담고 있으며, 워킹 디렉터리 안에 있는 파일들은 운영체제가 접근하여 수정할 수 있습니다.  
개발자가 직접 코드에 접근할 수 있는 파일들은 워킹 디렉터리 안에 있는 파일들로 제한됩니다. 
즉, 워킹 디렉터리는 사용자 작업 공간이라고 생각하면 됩니다. 

하지만, 워킹 디렉터리 영역에서 파일을 추가하거나, 수정했다고 해서 모든 파일을 `깃이 자동으로 관리해 주지는 않습니다`. 
워킹 디렉터리안에 생성된 파일의 초기 상태는 `추적되지 않음(untracked)`입니다.  

추적 되지 않음이란? 이 파일이 깃에 의해서 `이력 관리하지 않는 파일`이라는 뜻 입니다. 
따라서 깃에 의해서 이력을 관리 받기 위해서는 깃에게 추적 관리 해 달라고 `tracked 상태`로 변경해 주어야만 합니다. 
이를 `스테이지 영역`에 `등록` 한다고 말합니다.

즉, 스테이지 영역에 등록 되지 않은 파일들을 untracted 상태라고 합니다. 
깃에게 통보되지 않은 untracted 상태의 파일들은 깃에서 따로 관리 하지 않습니다.  

<br>

## tracked 상태  
---
실제로 개발 작업을 할 때 워킹 디렉터리의 파일들은 아주 `빈번하게 수정`됩니다. 
워킹 디렉터리 안에는 수많은 파일들과 `이력을 관리하지 않아도 되는 불필요한 파일`과 `작업`들이 같이 존재합니다. 
이런경우 깃 입장에서는 어떤 파일이 정말로 추적 관리가 필요한지 알 수 없습니다. 

깃은 추적하여 관리해야 하는 파일들은 `tracked` 상태로 표시합니다. tracked 상태는 untracted 상태의 반대 입니다. 
반면에 이력을 관리할 필요가 없는 파일들은 `untracked` 상태로 두는 것입니다. 
워킹 디렉터리안에 새로 생성된 파일들은 기본적으로 `추적되지 않음(untracked)` 상태입니다.

`untracted` 상태의 파일들을 `스테이지 영역`에 `등록`이라는 과정을 수행하게 되면 `tracked` 상태로 변경됩니다.  
스테이지에 등록을 하는 방법은 깃의 `add`명령을 사용하는 것입니다. 
`add`명령의 사용법은 다음에 자세히 설명 하도록 하겠습니다. 
먼저 `add` 명령어를 실행하여 추적 상태로 변경 형태를 다음과 같이 그림으로 이해해 볼 수 있습니다.   
 
![깃_워킹디렉터리](./img/working_directory.jpg) 

이렇게 워킹디렉터리와 스테이지 영역 사이에 tracked와 untracted 라는 개념을 도입하는 것은 깃이 수많은 파일들의 이력을 효율적으로 
관리하기 위해서 입니다. 이를 이용하지 않고 모든 파일의 상태를 모니터링 하여 기록을 한다면 시스템에 엄청난 부하가 발생됩니다.  

개발자에게 관리할 파일 목록들을 제출해 달라고 요청하는 것이 더 현명합니다. 
따라서 깃은 요청받은 파일들만 추적 관리합니다. 이렇게 관리할 파일 목록에 등록된 상태를 추적 상태라고 합니다.  



<br><br>