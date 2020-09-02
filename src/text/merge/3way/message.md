---
layout: home
title: "3-way 병합"
keyword: "3-way 병합"
breadcrumb:
- "text"
- "merge"
- "message"
---

## 병합 메시지
---
3-way 병합을 간단히 실습해 보았습니다. 앞에서 3-way 병합을 할 때 새로운 병합 커밋이 생성되었습니다. 3-way 병합은 Fast-Forward 병합과 달리 병합 메시지가 필요합니다. 그리고 “Merge branch ‘hotfix’”라고 커밋 메시지가 자동 삽입된 것을 확인할 수 있습니다. 깃은 두 브랜치를 병합한 후에 새로운 커밋을 하면서 동시에 메시지를 자동 생성합니다.  

자동으로 작성되는 메시지 외에 직접 커밋 메시지를 작성할 수도 있습니다. merge 명령어를 실행할 때 -e 또는 --edit 옵션을 사용하면 됩니다.  

```
$ git merge 브랜치이름 --edit
```

그럼 직접 병합 메시지를 작성해 봅시다. 실습을 위해 바로 앞에서 진행한 병합을 취소하고 메시지를 추가하여 다시 병합하겠습니다. reset 명령어로 바로 앞의 병합을 취소할 수 있습니다. 리셋은 9장에서 자세히 설명하겠습니다.   

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git reset --hard HEAD^ ☜ 병합을 취소합니다.
HEAD is now at 8583edf add menu4

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git merge hotfix --edit
```

개발자가 직접 입력할 수 있는 vi 에디터 창이 열립니다.  

그림 8-22] 병합 메시지를 입력할 수 있는 vi 에디터 창  
![병합 메시지를 입력할 수 있는 vi 에디터 창](./img/08-22.jpg)

병합 메시지를 작성하고 에디터를 종료합니다. 그러면 다음과 같이 병합 결과 메시지가 출력되고 직접 작성한 메시지로 커밋됩니다.  

```
Auto-merging index.htm
Merge made by the 'recursive' strategy.
 index.htm | 3 +++
 1 file changed, 3 insertions(+)

```

<br><br>