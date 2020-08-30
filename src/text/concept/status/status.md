---
layout: home
title: "상태확인"
keyword: "상태 확인"
breadcrumb:
- "text"
- "concept"
- "status"
---

# status 명령어로 깃 상태 확인
---
파일을 `생성`하고 `수정`한다는 것은 변화를 의미합니다. 또 이러한 변화들은 `순서`가 있습니다. 

<br>

## 변화를 감지
---
깃은 각 저장 영역에서 일어나는 다양한 변화를 감시합니다.  
그리고 이러한 변화를 감지하고 `상태 메시지`를 출력합니다.  

status 명령어를 사용하면 깃의 상태 메시지를 확인할 수 있습니다.  
특히 status 명령어는 많이 사용하는 깃 명령어 중 하나입니다.  

<br>

## 명령어 실습
---
터미널(깃 배시)에서 status 명령어를 입력합니다.  

```
$ git status ☜ 상태를 확인하는 명령.
On branch master
No commits yet ☜커밋이 없다는 메시지
nothing to commit (create/copy files and use "git add" to track) ☜변경된 내용이 없다는 메시지
```

우리는 처음 깃 저장소를 생성하고, 실습 이후에 아무 작업도 하지 않았습니다.  

status 명령어를 실행하면 이처럼 `변경된 내용과 커밋이 없다고 메시지`를 출력할 것입니다.  
나중에 커밋 명령을 수행하면 status 명령어로 파일들의 변경된 상태를 확인할 수 있습니다.  

<br>
