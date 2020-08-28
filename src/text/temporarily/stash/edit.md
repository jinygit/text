---
layout: git
title: "스태시"
keyword: "스태시, stash"
---

## 새 코드 작성 중 기존 코드를 수정
---
앞의 상황에 이어 또 다른 상황을 고려해 보겠습니다.

* 상황 2  
기존 코드를 수정하는 도중에 또 다른 수정 요청이 들어옵니다. 기존 코드에 버그가 발견되어 요청된 긴급 수정 건입니다. 작업 중인 브랜치는 잠시 멈추고, 버그를 수정하려면 다른 브랜치에서 작업해야 합니다. 즉, 두 브랜치 작업을 동시에 수행해야 합니다.  

현재 브랜치는 작업 중인 코드로 불완전합니다. 새롭게 발견된 버그를 수정하려면 또 다른 원본 브랜치가 필요합니다. 원본 master 브랜치에서 새로운 브랜치를 생성해야 합니다. 따라서 master 브랜치로 체크아웃합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy07 (feature)
$ git checkout master
error: Your local changes to the following files would be overwritten by checkout:
        stash.htm
Please commit your changes or stash them before you switch branches.
Aborting
```

앗, 원본 master 브랜치로 체크아웃되지 않습니다! 오류 메시지만 출력됩니다. 오류 메시지 내용은 워킹 디렉터리에 커밋하지 않은 작업이 남아 있어 현재 브랜치를 변경할 수 없다는 것입니다.  

이러한 오류는 현재 수정하는 작업들이 체크아웃으로 다른 브랜치의 워킹 디렉터리에 영향을 줄 수 있기 때문입니다. 깃은 이러한 충돌을 미연에 방지하고자 작업 중인 내용이 있을 때는 브랜치 간 이동을 제한합니다.  

브랜치를 변경하기 위한 체크아웃을 하려면 현재 작업 중인 워킹 디렉터리와 스테이지를 깔끔히 정리해야 합니다. 하지만 아직은 새로운 기능의 작업이 완료되지 않아 커밋할 수 없습니다. 이때 스태시를 활용하면 매우 유용합니다.  

<br>